Reakce na https://retrocip.cz/jednodeskova-vyzva-prvni-kolo/

Autor: V. Lieberzeit
       vladimir.lieberzeit@gmail.com

Licence: Creative Commons

Soubory:
========
* monitor.z80: Jednoduchý monitor pro Z-80.
* test.z80: Testovací uživatelský program, spouštěný a laděný monitorem.
          Pro jednoduchost je tento kód už přednačten na adrese 8000h.
* mycomputer.emu: Konfigurační soubor pro https://www.asm80.com,
          pomocí kterého byl monitor laděn a testován.

Předpokládá se, že uživatelské programy budou používat RAM 8000h-82FFh.
Monitor má primitivní editor příkazové řádky: BS=smaž poslední znak,
ESC=smaž všechny znaky.

Implementované příkazy:
=======================
RD n    - Zobrazí obsah 256-bytového bloku uživatelské RAM, n=0..3
WR aaaa xxyyzz... - Do RAM od adresy aaaa uloží byty xx,yy,zz,...
G aaaa [bbbb] - Spustí kód od adresy aaaa, volitelně s breakpointem
          na adrese bbbb
C [bbbb] - Pokračuje ve vykonávání kódu od aktuálního PC, volitelně
          s breakpointem na adrese bbbb
R       - Zobrazí obsah CPU registrů
AF|BC|DE|HL|IX|IY|SP|PC=xxxx - Nastaví hodnotu daného registru na xxxx

Zvažoval jsem ještě načtení uživatelského programu v Intel HEX formátu,
ale protože do ASM80.COM nejde udělat copy&paste (alespoň já jsem nepřišel
na to jak), tak jsem to opustil jako kontraproduktivní. Přepisovat HEX
ručně je blbost.
