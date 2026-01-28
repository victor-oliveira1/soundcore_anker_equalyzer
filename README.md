# 🎧 Soundcore P20i EQ Controller (Desktop)

Uma ferramenta leve em Python para controlar o equalizador dos fones **Anker Soundcore P20i** (pode funcionar com outros modelos da marca) diretamente pelo computador via Bluetooth.

Como o aplicativo oficial da Soundcore está disponível apenas para dispositivos móveis, este projeto utiliza engenharia reversa sobre o protocolo **RFCOMM (Bluetooth Classic)** para liberar o controle de áudio no Windows, Linux ou macOS.

---

## ✨ Funcionalidades

* **Acesso Direto:** Altera a equalização sem precisar desconectar do PC e usar o celular.
* **Presets Oficiais:** Inclui todas as 22 curvas de áudio originais da Anker (Bass Booster, Podcast, Rock, etc.).
* **Minimalista:** Sem interface pesada, apenas um script socket rápido e eficiente.

---

## 🛠️ Como Funciona

O Soundcore P20i utiliza um canal serial Bluetooth (RFCOMM) na **porta 10** para receber comandos de configuração. Através de análise de tráfego (HCI Snoop), identificamos que os pacotes seguem o padrão proprietário da Anker:

`08ee 0000 0002 8320 ... [ID_PRESET] ... [PAYLOAD_BANDAS] ... [CHECKSUM]`



---

## 🚀 Como Usar

### 1. Pré-requisitos
* **Python 3.9+** instalado.
* Fone pareado com o computador.
* **Importante:** Desconecte o fone do aplicativo Soundcore no celular antes de usar (o canal RFCOMM permite apenas uma conexão ativa por vez).

### 2. Configuração
Abra o arquivo `p20i_eq.py` e altere a variável `addr` com o endereço MAC do seu fone (você pode encontrá-lo nas configurações de Bluetooth do seu OS):
```
addr = "18:9C:2C:XX:XX:XX" # Substitua pelo MAC do seu fone
```

### 3. Execução
Execute o script passando o nome do preset desejado como argumento:
```
python p20i_eq.py soundcore_bass
```

---
## 🎹 Presets Disponíveis

Você pode utilizar qualquer um dos seguintes termos como argumento:
||||
|:---|:---:|---:|
|soundcore|soundcore_bass|acustica|
|redutor_graves|classico|podcast|
|danca|deep|eletronica|
|flat|hip_hop|jazz|
|latina|lounge|piano|
|pop|r&b|rock|
|palavra|redutor_agudos|amplificador_agudos|

---

## ⚠️ Aviso Legal
Este projeto não possui vínculo oficial com a Anker ou a marca Soundcore. Ele foi desenvolvido exclusivamente para fins educacionais e de conveniência pessoal através de análise de protocolo e engenharia reversa.

---

## 💡 Próximos Passos
Pretendo implementar as seguintes melhorias:

* [ ] **Interface gráfica (GUI):** Criar uma janela com sliders para facilitar o uso.
* [ ] **EQ Customizado:** Implementar o cálculo de Checksum dinâmico para permitir qualquer ajuste de frequência.
* [ ] **Auto-discovery:** Sistema para encontrar o endereço MAC do fone automaticamente.

Contribuições são muito bem-vindas! Sinta-se à vontade para abrir uma Issue ou enviar um Pull Request.
