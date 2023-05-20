# Cvičení: Autentizace a POST

Domácí úkol pro kurz JavaScript 2 od Czechitas.

## 1. Obnova seznamu

Naše aplikace *Nákupy* ještě neumí mazat položky seznamu. Když nám nákupní seznam příliš naroste, zatím to vyřešíme tak, že umožníme seznam vrátit do původní podoby tak, jak vypadal při prvním přihlášení. Do komponenty `ShopList` přidáme tlačítko, které odešle požadavek na obnovu seznamu na server pomocí POST a překreslí komponentu.

- Vyjděte z kódu aplikace vytvořené na lekci. Použijte repozitář [projekt-nakupy-post](https://github.com/Czechitas-podklady-WEB/projekt-nakupy-post) jako šablonu pro vytvoření vlastního repozitáře, který si naklonujte.
- Do hlavičky v komponentě `ShopList` přidejte HTML pro panel s tlačítkem *obnovit*. Hlavička komponenty pak bude vypadat takto:

```html
<div class="shoplist__head">
  <h2 class="shoplist__day">${dayName}</h2>
  <div class="shoplist__toolbar">
    <button class="reset-btn">obnovit</button>
  </div>
</div>
```

- Vytvořte posluchač události `handleReset` a připojte jej na tlačítko. Je to velmi podobné tomu, jak je vytvořen posluchač `handleSubmit`. Do vašeho posluchače zatím dejte například `console.log`, a vyzkoušejte, že funguje.
- Nyní je potřeba odeslat požadavek na server. Zkontrolujte si, že máte v local storage uložený správný token. Zavolejte funkci `fetch`, která na adresu

```javascript
https://nakupy.kodim.app/api/me/week/:day/actions
```

odešle JSON ve tvaru

```javascript
{
  "type": "reset"
}
```

Tento API endpoint vrátí obnovený obsah celého seznamu. Je tedy potřeba celou komponentu `ShopList` překreslit, podobně jako to děláme při přidávání nového prvku.
- Vyzkoušejte, že vaše aplikace funguje a že je možné pomocí tlačítka *obnovit* vrátit seznamy do původní podoby.

## 2. Vymazání seznamu položek

Pokračujte v aplikaci z předchozího příkladu. Rozšíříme náš nákupní seznam ještě o tlačítko *vymazat*, které naopak umožní odstranit najednou všechny položky seznamu.

Postup je velmi podobný jako v předchozím cvičení.

- Do prvku `shoplist__toolbar` přidejte tlačítko *vymazat* s třídou `clear-btn`.
- Založte posluchač události `handleClear` a vyzkoušejte, že se zavolá při stisknutí tlačítka.
- V obsluze události pošlete autentizovaný POST požadavek na stejnou adresu jako v předchozím příkladu

```javascript
https://nakupy.kodim.app/api/me/week/:day/actions
```

Tentokrát je třeba odeslat toto JSON *body*:

```javascript
{
  "type": "clear"
}
```

- Opět vyzkoušejte, že aplikace funguje, a že můžete seznamy hravě mazat nebo obnovovat zcela dle libosti.
