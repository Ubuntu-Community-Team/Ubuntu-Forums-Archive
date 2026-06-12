---
title: "Ubuntu 12.4 no troba xarxes wifi"
date: 2012-11-23
forum: Catalan Team
---

### Post by jesús sol on 2012-11-23
[FONT=FreeSans, sans-serif]Salut! Acabo de comprar un portàtil nou. El vell ja feia figa. És un Dell Vostro 3560, L'he posat en marxa, he engegat el guindous i tot seguit, amb un disc de l'ubuntu 12.4, he tret el guindous i he posat el pangolin. 
En reiniciar, he vist que no havia quedat tot en català. Ja ho arreglarem. Però a l'hora de navegar, no apareix cap xarxa de wifi. (Amb el guindous anava bé!). Total, que no em puc connectar. Em podeu ajudar? :(
Gràcies![/FONT]
 [FONT=FreeSans, sans-serif]Jesús[/FONT]

---

### Post by wgarcia on 2012-11-24
Enganxa el retorn que dóna la següent instrucció des d'una terminal:

```
lspci |grep Network
```

---

### Post by jesús sol on 2012-11-24
Bon dia, Wgarcia!
diu això:
08:00.0 Network controller: Broadcom Corporation Device 4365 (rev 01)
gràcies!

---

### Post by wgarcia on 2012-11-24
La targeta wifi que tens necessita un controlador privatiu, que té problemes amb les versions més noves d'Ubuntu (bé, en realitat amb els nuclis de Linux més nous, així que no és un problema exclusiu d'Ubuntu9).  Està en camí de solució però encara no està del tot solucionat, tinc entès. 

Tens dues opcions en el meu parer:

1) Fer una instal·lació nova amb la versió 11.10, que té suport fins a abril de 2013, i esperar que el problema ja s'hagi solucionat en aquell moment. Em sembla que aquest problema va aparèixer amb el nucli que porta la versió 12.04.

2) Intentar instal·lar uns controladors que s'han preparat per als nuclis més nous. Per això es necessiten dues coses: a) que identifiquis si tens el sistema de 32 bits o 64 bits, cosa que pots mirar des d'una terminal entrant la instrucció "uname -m", si veus "i686" és 32 bits, i si veus "x86_64" és 64 bits. b) Aconseguir una connexió temporal a Internet per cable a l'ordinador per baixar-se uns paquets, o tenir un altre ordinador on puguis baixar els paquets i copiar-los a l'ordinador.

---

### Post by jesús sol on 2012-11-24
ok!! diu:i686, o sia, 32 bits. Ara tinc el Dell connectat amb cable i navega.
gràcies!:)

---

### Post by wgarcia on 2012-11-24
Hi ha un missatge a AskUbuntu on apunten tots els que tenen el teu problema:

[http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)

Segons aquest missatge aquí es proveeix un controlador per a la teva targeta wifi. O sigui que sense garanties, ho dic perquè jo no he instal·lat aquests paquets però hi ha molts fòrums que apunten aquí, pots provar a veure si funciona.

Per instal·lar-lo, des d'una terminal primer instal·la els prerequisits:

```
sudo apt-get install linux-headers$(uname -r | grep -Po "\-[a-z].*")
sudo apt-get install build-essential dkms
```

Després baixa el paquet a la teva carpeta d'inici:

[https://www.dropbox.com/s/n76dcsdtayvp0wm/wireless-bcm43142-dkms-6.20.55.19_i386.deb](https://www.dropbox.com/s/n76dcsdtayvp0wm/wireless-bcm43142-dkms-6.20.55.19_i386.deb)

Un cop fet això obre una terminal i entra:

```
sudo dpkg -i *.deb
```

Això hauria d'instal·lar el controlador, a veure què tal. Per provar-ho has de reiniciar el sistema i fer:

```
sudo modprobe wl
```

Si funciona ja veurem com carregar-ho permanentment.

---

### Post by jesús sol on 2012-11-24
...he fet tot el conjur que m'has dit. Semblava que tot prou bé, però al final, diu això;
sudo modprobe wl
[sudo] password for jesus: 
FATAL: Module wl not found.

---

### Post by wgarcia on 2012-11-24
Si has fet tot això a la teva carpeta d'inici, a veure quin retorn et dóna la següent instrucció:

```
find . -name wl.ko
```

---

### Post by jesús sol on 2012-11-24
...no diu res :(
jesus@jesus-Dell:~$ 
jesus@jesus-Dell:~$ find . -name wl.ko
jesus@jesus-Dell:~$ 
quan dius la carpeta d'inici, vols dir la "carpeta de l'usuari? és allà on ho he baixat...

---

### Post by wgarcia on 2012-11-25
Mira a veure si la instrucció "dpkg -i *.deb" et va crear algun fitxer que tingui extensió "ko" en la teva carpeta d'usuari. Aquest seria el mòdul que s'hauria creat i s'hauria de carregar al nucli. Per veure els fitxers creats o bé navegues o pots donar la instrucció "ls" des del terminal i et mostrarà els fitxers i carpetes que hi ha.

---

### Post by jesús sol on 2012-11-25
el terminal diu això:
jesus@jesus-Dell:~$ ls
Baixades          Imatges     Vídeos
Documents         Música      wireless-bcm43142-dkms-6.20.55.19_i386.deb
Escriptori        Plantilles
examples.desktop  Públic

a la meva carpeta hi ha aquest fitxer, /home/jesus/wireless-bcm43142-dkms-6.20.55.19_i386.deb
Si l'obro surt el centre de programari d'ubuntu i diu que està instal·lat.

no trobo cap fitxer .ko
gràcies per la teva paciència. Sóc prou ignorant amb aquestes coses...

---

### Post by wgarcia on 2012-11-25
Doncs continuem la tasca detectivesca a veure si trobem si s'ha instal·lat algun mòdul nou. Sisplau proveeix ara el retorn de la següent instrucció:

```
ls /lib/modules/`uname -r`/kernel/drivers/net/wireless
```

---

### Post by jesús sol on 2012-11-25
uau!! guaita quines coses respon la bèstia!
jesus@jesus-Dell:~$ ls /lib/modules/`uname -r`/kernel/drivers/net/wireless
adm8211.ko       atmel_pci.ko  iwlwifi            orinoco        rtlwifi
airo_cs.ko       b43           iwmc3200wifi       p54            wl1251
airo.ko          b43legacy     libertas           prism54        wl12xx
at76c50x-usb.ko  brcm80211     libertas_tf        ray_cs.ko      wl3501_cs.ko
ath              hostap        mac80211_hwsim.ko  rndis_wlan.ko  zd1201.ko
atmel_cs.ko      ipw2x00       mwifiex            rt2x00         zd1211rw
atmel.ko         iwlegacy      mwl8k.ko           rtl818x
jesus@jesus-Dell:~$

---

### Post by wgarcia on 2012-11-25
Suposo que has reiniciat després d'allò de "dpkg -i .deb", oi?

---

### Post by jesús sol on 2012-11-25
oitant! immediatament! i després unes quantes vegades.

---

### Post by wgarcia on 2012-11-26
Dons seguim buscant. 

Sisplau prova ara a veure si podem esbrinar si el mòdul, que em sembla que s'hauria de dir wl.ko, està en alguna subcarpeta del directori de mòduls. Per això ara podem provar la instrucció d'abans amb "tree", que fa una llista de carpetes i subcarpetes, però abans s'haurà d'instal·lar:

```
sudo apt-get install tree
```

i després:

```
tree /lib/modules/`uname -r`/kernel/drivers/net/wireless
```

---

### Post by jesús sol on 2012-11-26
vergesanta! la de coses que hi ha!:
jesus@jesus-Dell:~$ tree /lib/modules/`uname -r`/kernel/drivers/net/wireless
/lib/modules/3.2.0-33-generic-pae/kernel/drivers/net/wireless
&#9500;&#9472;&#9472; adm8211.ko
&#9500;&#9472;&#9472; airo_cs.ko
&#9500;&#9472;&#9472; airo.ko
&#9500;&#9472;&#9472; at76c50x-usb.ko
&#9500;&#9472;&#9472; ath
&#9474;   &#9500;&#9472;&#9472; ath5k
&#9474;   &#9474;   &#9492;&#9472;&#9472; ath5k.ko
&#9474;   &#9500;&#9472;&#9472; ath6kl
&#9474;   &#9474;   &#9492;&#9472;&#9472; ath6kl.ko
&#9474;   &#9500;&#9472;&#9472; ath9k
&#9474;   &#9474;   &#9500;&#9472;&#9472; ath9k_common.ko
&#9474;   &#9474;   &#9500;&#9472;&#9472; ath9k_htc.ko
&#9474;   &#9474;   &#9500;&#9472;&#9472; ath9k_hw.ko
&#9474;   &#9474;   &#9492;&#9472;&#9472; ath9k.ko
&#9474;   &#9500;&#9472;&#9472; ath.ko
&#9474;   &#9492;&#9472;&#9472; carl9170
&#9474;       &#9492;&#9472;&#9472; carl9170.ko
&#9500;&#9472;&#9472; atmel_cs.ko
&#9500;&#9472;&#9472; atmel.ko
&#9500;&#9472;&#9472; atmel_pci.ko
&#9500;&#9472;&#9472; b43
&#9474;   &#9492;&#9472;&#9472; b43.ko
&#9500;&#9472;&#9472; b43legacy
&#9474;   &#9492;&#9472;&#9472; b43legacy.ko
&#9500;&#9472;&#9472; brcm80211
&#9474;   &#9500;&#9472;&#9472; brcmfmac
&#9474;   &#9474;   &#9492;&#9472;&#9472; brcmfmac.ko
&#9474;   &#9500;&#9472;&#9472; brcmsmac
&#9474;   &#9474;   &#9492;&#9472;&#9472; brcmsmac.ko
&#9474;   &#9492;&#9472;&#9472; brcmutil
&#9474;       &#9492;&#9472;&#9472; brcmutil.ko
&#9500;&#9472;&#9472; hostap
&#9474;   &#9500;&#9472;&#9472; hostap_cs.ko
&#9474;   &#9500;&#9472;&#9472; hostap.ko
&#9474;   &#9500;&#9472;&#9472; hostap_pci.ko
&#9474;   &#9492;&#9472;&#9472; hostap_plx.ko
&#9500;&#9472;&#9472; ipw2x00
&#9474;   &#9500;&#9472;&#9472; ipw2100.ko
&#9474;   &#9500;&#9472;&#9472; ipw2200.ko
&#9474;   &#9492;&#9472;&#9472; libipw.ko
&#9500;&#9472;&#9472; iwlegacy
&#9474;   &#9500;&#9472;&#9472; iwl3945.ko
&#9474;   &#9500;&#9472;&#9472; iwl4965.ko
&#9474;   &#9492;&#9472;&#9472; iwl-legacy.ko
&#9500;&#9472;&#9472; iwlwifi
&#9474;   &#9492;&#9472;&#9472; iwlwifi.ko
&#9500;&#9472;&#9472; iwmc3200wifi
&#9474;   &#9492;&#9472;&#9472; iwmc3200wifi.ko
&#9500;&#9472;&#9472; libertas
&#9474;   &#9500;&#9472;&#9472; libertas_cs.ko
&#9474;   &#9500;&#9472;&#9472; libertas.ko
&#9474;   &#9500;&#9472;&#9472; libertas_sdio.ko
&#9474;   &#9500;&#9472;&#9472; libertas_spi.ko
&#9474;   &#9492;&#9472;&#9472; usb8xxx.ko
&#9500;&#9472;&#9472; libertas_tf
&#9474;   &#9500;&#9472;&#9472; libertas_tf.ko
&#9474;   &#9492;&#9472;&#9472; libertas_tf_usb.ko
&#9500;&#9472;&#9472; mac80211_hwsim.ko
&#9500;&#9472;&#9472; mwifiex
&#9474;   &#9500;&#9472;&#9472; mwifiex.ko
&#9474;   &#9500;&#9472;&#9472; mwifiex_pcie.ko
&#9474;   &#9492;&#9472;&#9472; mwifiex_sdio.ko
&#9500;&#9472;&#9472; mwl8k.ko
&#9500;&#9472;&#9472; orinoco
&#9474;   &#9500;&#9472;&#9472; orinoco_cs.ko
&#9474;   &#9500;&#9472;&#9472; orinoco.ko
&#9474;   &#9500;&#9472;&#9472; orinoco_nortel.ko
&#9474;   &#9500;&#9472;&#9472; orinoco_plx.ko
&#9474;   &#9500;&#9472;&#9472; orinoco_tmd.ko
&#9474;   &#9500;&#9472;&#9472; orinoco_usb.ko
&#9474;   &#9492;&#9472;&#9472; spectrum_cs.ko
&#9500;&#9472;&#9472; p54
&#9474;   &#9500;&#9472;&#9472; p54common.ko
&#9474;   &#9500;&#9472;&#9472; p54pci.ko
&#9474;   &#9500;&#9472;&#9472; p54spi.ko
&#9474;   &#9492;&#9472;&#9472; p54usb.ko
&#9500;&#9472;&#9472; prism54
&#9474;   &#9492;&#9472;&#9472; prism54.ko
&#9500;&#9472;&#9472; ray_cs.ko
&#9500;&#9472;&#9472; rndis_wlan.ko
&#9500;&#9472;&#9472; rt2x00
&#9474;   &#9500;&#9472;&#9472; rt2400pci.ko
&#9474;   &#9500;&#9472;&#9472; rt2500pci.ko
&#9474;   &#9500;&#9472;&#9472; rt2500usb.ko
&#9474;   &#9500;&#9472;&#9472; rt2800lib.ko
&#9474;   &#9500;&#9472;&#9472; rt2800pci.ko
&#9474;   &#9500;&#9472;&#9472; rt2800usb.ko
&#9474;   &#9500;&#9472;&#9472; rt2x00lib.ko
&#9474;   &#9500;&#9472;&#9472; rt2x00pci.ko
&#9474;   &#9500;&#9472;&#9472; rt2x00usb.ko
&#9474;   &#9500;&#9472;&#9472; rt61pci.ko
&#9474;   &#9492;&#9472;&#9472; rt73usb.ko
&#9500;&#9472;&#9472; rtl818x
&#9474;   &#9500;&#9472;&#9472; rtl8180
&#9474;   &#9474;   &#9492;&#9472;&#9472; rtl8180.ko
&#9474;   &#9492;&#9472;&#9472; rtl8187
&#9474;       &#9492;&#9472;&#9472; rtl8187.ko
&#9500;&#9472;&#9472; rtlwifi
&#9474;   &#9500;&#9472;&#9472; rtl8192c
&#9474;   &#9474;   &#9492;&#9472;&#9472; rtl8192c-common.ko
&#9474;   &#9500;&#9472;&#9472; rtl8192ce
&#9474;   &#9474;   &#9492;&#9472;&#9472; rtl8192ce.ko
&#9474;   &#9500;&#9472;&#9472; rtl8192cu
&#9474;   &#9474;   &#9492;&#9472;&#9472; rtl8192cu.ko
&#9474;   &#9500;&#9472;&#9472; rtl8192de
&#9474;   &#9474;   &#9492;&#9472;&#9472; rtl8192de.ko
&#9474;   &#9500;&#9472;&#9472; rtl8192se
&#9474;   &#9474;   &#9492;&#9472;&#9472; rtl8192se.ko
&#9474;   &#9492;&#9472;&#9472; rtlwifi.ko
&#9500;&#9472;&#9472; wl1251
&#9474;   &#9500;&#9472;&#9472; wl1251.ko
&#9474;   &#9500;&#9472;&#9472; wl1251_sdio.ko
&#9474;   &#9492;&#9472;&#9472; wl1251_spi.ko
&#9500;&#9472;&#9472; wl12xx
&#9474;   &#9500;&#9472;&#9472; wl12xx.ko
&#9474;   &#9500;&#9472;&#9472; wl12xx_sdio.ko
&#9474;   &#9492;&#9472;&#9472; wl12xx_spi.ko
&#9500;&#9472;&#9472; wl3501_cs.ko
&#9500;&#9472;&#9472; zd1201.ko
&#9492;&#9472;&#9472; zd1211rw
    &#9492;&#9472;&#9472; zd1211rw.ko

35 directories, 86 files
jesus@jesus-Dell:~$

---

### Post by wgarcia on 2012-11-26
Anem a veure quin d'aquests està usant el sistema. Per això fes:

```
lsmod | grep -i wifi
```

ens ho mostrarà.

---

### Post by jesús sol on 2012-11-26
no diu res?
jesus@jesus-Dell:~$ lsmod | grep -i wifi
jesus@jesus-Dell:~$ 
jesus@jesus-Dell:~$ jesus@jesus-Dell:~$ lsmod | grep -i wifi
jesus@jesus-Dell:~$: no s'ha trobat l'ordre
jesus@jesus-Dell:~$ jesus@jesus-Dell:~$

---

### Post by wgarcia on 2012-11-26
Curiós, pensava que aquestes instruccions eren part de programes del sistema. Pots mirar que diu si fas:

```
sudo apt-get install grep
```

i tornes a provar en cas que no tinguessis instal·lat "grep"?

---

### Post by jesús sol on 2012-11-26
diu això:
jesus@jesus-Dell:~$ sudo apt-get install grep
[sudo] password for jesus: 
S'està llegint la llista de paquets&#8230; Fet 0%
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet%
grep ja es troba en la versió més recent.
0 actualitzats, 0 nous a insta&#320;lar, 0 a suprimir i 0 no actualitzats.
jesus@jesus-Dell:~$

---

### Post by Satboy on 2012-11-29
Bon dia,
 Jo tinc una targeta wifi Broadcom.En el meu cas, però, se'm ha instal·lat tota soleta fent servir el **Linux Mint 13** (Katya)
 L'has provat?
 El **Mint** està basat en **Ubuntu**.

 Dew! ;)

---

### Post by wgarcia on 2012-11-29
Sí, a l'Ubuntu també se sol instal·lar sola, però el problema és que per aquest model en particular el controlador propietari no s'ha actualitzat i està donant problemes, segons he pogut llegir, a totes les distribucions de Linux.

---

### Post by jesús sol on 2012-11-29
Ei! gràcies per el vostre interès i ajut. Entenc que el problema no té solució, amb Precise Pangolin. PP, -les inicials ja tenen mala pinta- :D
Ja és trist el meu cas. Despres d'uns quants anys amb un portàtil que només podia funcionar connectat al corrent, -no carregava la bateria- finalment en puc comprar un de nou, i ara no em puc moure del costat del mòdem! :( 
Suposo que el que haig de fer, és posar-hi el Lucid Lynx, Però no sé com fer-ho. S'ha d'esborrar el Pangolin?, com?
Agraït,
Jesús

---

### Post by jesús sol on 2012-12-08
despres d'una setmana de donar-hi voltes, he tornat a començar amb la instal·lació del controlador que em vas dir. I diu el següent:
jesus@jesus-Dell:~$ sudo dpkg -i *.deb
[sudo] password for jesus: 
dpkg-deb: error: «wireless-bcm43142-dkms-6.20.55.19_amd64.deb» no és un arxiu amb el format debian
dpkg: s'ha produït un error en processar wireless-bcm43142-dkms-6.20.55.19_amd64.deb (--install):
 el subprocés dpkg-deb --control retornà el codi d'eixida d'error 2
(S'està llegint la base de dades&#8230; hi ha 199019 fitxers i directoris insta&#320;lats actualment.)
S'està preparant per a reemplaçar wireless-bcm43142-oneiric-dkms 6.20.55.19~bdcom0602.0400.1000.0400-0somerville1 (fent servir wireless-bcm43142-dkms-6.20.55.19_i386.deb)&#8230;
Removing all DKMS Modules
Done.
S'està desempaquetant el reemplaçament de wireless-bcm43142-oneiric-dkms&#8230;
S'està configurant wireless-bcm43142-oneiric-dkms (6.20.55.19~bdcom0602.0400.1000.0400-0somerville1)&#8230;
Loading new wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400 DKMS files...
Building only for 3.2.0-34-generic-pae
Building for architecture i686
Building initial module for 3.2.0-34-generic-pae
Error! Bad return status for module build on kernel: 3.2.0-34-generic-pae (i686)
Consult /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
S'estan processant els activadors per a initramfs-tools&#8230;
update-initramfs: Generating /boot/initrd.img-3.2.0-34-generic-pae
S'han trobat errors en processar:
 wireless-bcm43142-dkms-6.20.55.19_amd64.deb
jesus@jesus-Dell:~$ 

cap més suggerència?
gràcies!

---

### Post by wgarcia on 2012-12-09
> dpkg-deb: error: «wireless-bcm43142-dkms-6.20.55.19_amd64.deb» no és un arxiu amb el format debian

Sembla que estàs intentant instal·lar el fitxer corresponent a 64 bits, però tu tens un sistema de 32 bits. Elimina aquest fitxer, i intenta tornar a l'enllaç on el vas baixar i baixa't el de 32 bits, que tindrà "i386" en comptes de "amd64" en el nom. I després intenta seguir tots els passos un altre cop.

---

### Post by jesús sol on 2012-12-09
mekatxisss! jo instal·lo el que baixa d'aquesta adreça: [https://www.dropbox.com/s/n76dcsdtayvp0wm/wireless-bcm43142-dkms-6.20.55.19_i386.deb](https://www.dropbox.com/s/n76dcsdtayvp0wm/wireless-bcm43142-dkms-6.20.55.19_i386.deb),  que és la que em vas donar. Però és el que ja vaig instal·lar el primer cop i es veu que deu ser de 64 :(

---

### Post by wgarcia on 2012-12-10
És estrany, perquè el nom del fitxer sí que té "i386". Ara mateix si obres una terminal i entres "ls" perquè et mostris els fitxers, es veu el fitxer amb "i386" o amb "amd64"?

---

### Post by jesús sol on 2012-12-10
diu això:
jesus@jesus-Dell:~$ ls
Baixades          Imatges     wireless-bcm43142-dkms-6.20.55.19_amd64.deb
Documents         Música      wireless-bcm43142-dkms-6.20.55.19_amd64.deb.1
Dropbox           Plantilles  wireless-bcm43142-dkms-6.20.55.19_i386.deb
Escriptori        Públic
examples.desktop  Vídeos
jesus@jesus-Dell:~$ 
??:-k

---

### Post by wgarcia on 2012-12-10
D'acord, fes llavors des de la terminal:

```
rm wireless-bcm43142-dkms-6.20.55.19_amd64*
``` 

perquè esborri els fitxers incorrectes "amd64" i després torna a fer això de

```
sudo dpkg -i *.deb
```

a veure què tal...

---

### Post by jesús sol on 2012-12-10
...i diu això:
jesus@jesus-Dell:~$ rm wireless-bcm43142-dkms-6.20.55.19_amd64*  
 jesus@jesus-Dell:~$ sudo rm wireless-bcm43142-dkms-6.20.55.19_amd64*  
 [sudo] password for jesus:  
 rm: no s’ha pogut eliminar «wireless-bcm43142-dkms-6.20.55.19_amd64*»: El fitxer o directori no existeix  
 jesus@jesus-Dell:~$ :  
 jesus@jesus-Dell:~$  
 jesus@jesus-Dell:~$ sudo dpkg -i *.deb  
 (S'està llegint la base de dades… hi ha 199046 fitxers i directoris insta&#320;lats actualment.)  
 S'està preparant per a reemplaçar wireless-bcm43142-oneiric-dkms 6.20.55.19~bdcom0602.0400.1000.0400-0somerville1 (fent servir wireless-bcm43142-dkms-6.20.55.19_i386.deb)…  
 Removing all DKMS Modules  
 Done.  
 S'està desempaquetant el reemplaçament de wireless-bcm43142-oneiric-dkms…  
 S'està configurant wireless-bcm43142-oneiric-dkms (6.20.55.19~bdcom0602.0400.1000.0400-0somerville1)…  
 Loading new wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400 DKMS files...  
 Building only for 3.2.0-34-generic-pae  
 Building for architecture i686  
 Building initial module for 3.2.0-34-generic-pae  
 Error! Bad return status for module build on kernel: 3.2.0-34-generic-pae (i686)  
 Consult /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/make.log for more information.  
 update-initramfs: deferring update (trigger activated)  
 S'estan processant els activadors per a initramfs-tools…  
 update-initramfs: Generating /boot/initrd.img-3.2.0-34-generic-pae  
 jesus@jesus-Dell:~$  
ho sento, wgarcia! espero que no et tornis boig! :p a mi em ve justet!
gràcies per la paciència!

---

