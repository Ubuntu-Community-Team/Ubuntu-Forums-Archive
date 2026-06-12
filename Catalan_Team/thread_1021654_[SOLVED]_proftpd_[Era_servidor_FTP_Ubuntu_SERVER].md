---
title: "[SOLVED] proftpd [Era: servidor FTP Ubuntu SERVER]"
date: 2008-12-25
forum: Catalan Team
---

### Post by carlesbm on 2008-12-25
Hola gent i bon nadal

tinc un problema amb el meu servidor i concretament amb l'aplicació FTP donat que hem donava problemes he probat ha reinstalat-la i m'apareix aquets missatge.


carles@Servidor:~$ sudo apt-get install --reinstall proftpd
sudo: unable to resolve host Servidor
[sudo] password for carles: 
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències       
Reading state information... Fet           
0 actualitzats, 0 nous a instal·lar, 1 reinstal·lats, 0 a eliminar i 0 no actualitzats.
1 no instal·lats o eliminats completament.
After this operation, 0B of additional disk space will be used.
Voleu continuar [S/n]? S
S'està configurant proftpd (1.3.1-6ubuntu1) ...
 * Starting ftp server proftpd                                                                                                        - warning: the DisplayFirstChdir directive is deprecated and will be removed in a future release.  Please use the DisplayChdir directive.
 - warning: unable to determine IP address of 'Servidor'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
                                                                                                                              [fail]
invoke-rc.d: initscript proftpd, action "start" failed.
dpkg: s'ha produït un error en processar proftpd (--configure):
 el subprocés post-installation script retornà el codi d'eixida d'error 1
S'han trobat errors en processar:
 proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
carles@Servidor:~$ 


Com ho puc solucionar?

Gracies

---

### Post by oriolsbd on 2008-12-26
Això podria ser un error del fitxer /etc/hosts. En no sé quins casos, l'Ubuntu hi deixa la ip de la teva màquina com a "DNS.màquina", i només hauria de ser "màquina" (en el teu cas, "Servidor").

Edita el fitxer:
```
sudo gedit /etc/hosts
```

A tot arreu on vegis "DNS.màquina", deixa-ho només com a "màquina", i torna-ho a provar. No aniria malament fer-te una còpia de seguretat del fitxer /etc/hosts abans d'editar-lo.

---

