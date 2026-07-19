# 🐟 Assistente Xianyu

> ⚠️ **Nota:** este repositório é uma vitrine do projeto — o código de
> implementação real (`Content.js`, `manifest.json`, a lógica da Edge
> Function em `supabase/functions/`, etc.) foi ocultado por privacidade e
> segurança, e não é commitado aqui. O que você vê é só este README,
> descrevendo o que a extensão faz.

Extensão de Chrome de **uso pessoal**, feita por [Filipe Oliveira](https://github.com/ooliveira-ops) 👨‍💻 para facilitar compras no [Goofish/Xianyu](https://www.goofish.com) 🇨🇳 (marketplace chinês de segunda mão) via [CSSBuy](https://www.cssbuy.com) 📦 (agente de compra/reenvio internacional).

Não é um produto público, não tem distribuição na Chrome Web Store e não foi feita para uso por terceiros — é uma ferramenta pessoal para o próprio fluxo de compras do autor.

## ✨ O que a extensão faz

- 💰 **Conversão de preço e custo desembarcado**: converte o preço em Yuan para Real e calcula o custo estimado real no Brasil, incluindo Imposto de Importação, ICMS ("por dentro"), despacho postal e taxa de serviço da CSSBuy.
- 📈 **Cotação ao vivo**: busca a cotação Yuan → Real atualizada via um backend próprio, com cache local e fallback para um valor manual/fixo.
- ✅ **Selo de confiança do vendedor**: classifica o vendedor (Confiável / Mediano / Perigoso / Neutro) com base em número de vendas, percentual de feedback e tempo de conta.
- 🤖 **Análise por IA**: envia a descrição do produto para um modelo de IA (via backend próprio) e devolve uma análise estruturada — identificação do produto, tamanho/especificações, sinais de defeito ou divergência, política de devolução e um veredito de confiança.
- 💬 **Chat de acompanhamento**: depois da análise, permite fazer perguntas de acompanhamento sobre o item (ex: comparação de preço, autenticidade).
- 🖼️ **Busca por imagem**: permite enviar uma foto de um produto e receber sugestões de termos de busca (ou código/SKU, quando identificável) para encontrar o item equivalente no Goofish.
- 🔎 **Busca flutuante PT → CN**: traduz automaticamente termos de busca em português para chinês antes de pesquisar no Goofish.
- 🔗 **Atalhos entre plataformas**: botão "Comprar na CSSBuy" na página do produto no Goofish, e "Ver na Xianyu" na página equivalente na CSSBuy.
- 🌙 **Modo escuro**: inversão de tema para o Goofish inteiro, com preferência salva entre sessões.

## 🏗️ Arquitetura (visão geral)

- 🧩 **Extensão de Chrome (Manifest V3)**: content script injetado nas páginas do Goofish e da CSSBuy, sem permissões além dos dois domínios necessários.
- ☁️ **Backend**: uma Supabase Edge Function que recebe as chamadas da extensão e conversa com a API da OpenAI (análise de texto/imagem, chat) e com uma fonte de cotação de câmbio.
- 🚫📊 **Sem coleta de dados**: a extensão não tem telemetria, analytics ou qualquer tipo de rastreamento — é só o fluxo direto entre a página, a extensão e o backend.

## 🔒 Por que o código não está aqui

Como é uma ferramenta de uso estritamente pessoal, os arquivos de implementação (incluindo a URL do backend) ficam fora do controle de versão público por precaução — mesmo o repositório sendo privado no momento, essa separação evita qualquer exposição acidental caso isso mude no futuro.
