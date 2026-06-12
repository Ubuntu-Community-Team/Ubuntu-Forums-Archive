---
title: "No s'apaga l'ordinador i torna al GRUB"
date: 2010-05-01
forum: Catalan Team
---

### Post by joaquimrubio on 2010-05-01
Dijous a la nit vaig actualitzar el KK a Lucid Lynx via Internet, sense problemes llevat que s'hi va estar tota la nit. Divendres no vaig estar al portàtil, que va restar engegat fins avui dissabte. Quan l'he volgut apagar, enlloc d'apagar-se,  torna al menú del grub.


He provat d'apagar-lo via consola escrivint 

sudo halt now 

i a continuació entrar la contrasenya quan me la demana, però passa al mateix, torna al menú GRUB.

He provat l'utilitat de recuperar paquets trencats i tampoc arregla el problema.

He provat el mode a prova d'errors i també torna al menú GRUB.

Al menú GRUB hi ha 2 kernels, el darrer acaba en 21 i és el que he fet servir.
L'anterior, que acaba en 20 no funciona, l'ordinador queda penjat amb el fons de pantalla del Lucid i res mes i les telces Ctrl + Alt + F.. per anar al mode consola no responen. Aquest cop no he sabut apagar-lo de cap més manera que desendollant el portàtil.

En els altres casos, al tornar al menu GRUB sí que puc apagar l'ordinador amb el w-7.

En el mode a prova d'errors m'avisa que no s'ha pogut carregat l'arxiu AppArmor profiles, no sé si té relació amb el problema que explico, l'he buscat al Google però no he entés res.

---

### Post by SiscoGarcia on 2010-05-01
i si amb el «recovery mode» tries l'opció «dpkg» per restaurar paquets trencats? jo ho provaria.

---

### Post by joaquimrubio on 2010-05-02
Gràcies Sisco.

Ho he provat però tampoc funciona.

---

### Post by joaquimrubio on 2010-05-15
He fet un grub cat i em surt això: 

joaquim@joaquim-laptop:~$ grub cat
El programa «grub» no està instal·lat actualment.  Podeu instal·lar-lo si escriviu:
sudo apt-get install grub
joaquim@joaquim-laptop:~$ GRUB cat
GRUB: command not found
joaquim@joaquim-laptop:~$ Grub cat
No command 'Grub' found, did you mean:
 Command 'grub' from package 'grub' (main)
Grub: command not found
joaquim@joaquim-laptop:~$ 


Dubtes:

Haig de reparar alguna cosa?

És recomanable provar el "sudo aptitude install grub"?

Cal desinstal·lar el grub actual abans d'instal·lar de nou el grub?

---

