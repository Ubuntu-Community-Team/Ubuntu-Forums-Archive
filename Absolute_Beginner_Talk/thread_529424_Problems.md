---
title: "Problems"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by sup3roque on 2007-08-19
well with the automatix2 I install the reaplayer

but follow one tutorial to play some files I try to install something like helix-player

some errors begin

then the update option was broken and say allways to do apt-get install -f

that's the result

sup3r@sup3r-laptop:~$ sudo apt-get install -f
A Ler Listas de Pacotes... Pronto
Construindo Árvore de Dependências       
Lendo informação de estado... Pronto
Corrigindo dependências... Feito
Os seguintes pacotes extra serão instalados:
  helix-player
Os seguintes NOVOS pacotes serão instalados:
  helix-player
0 pacotes actualizados, 1 pacotes novos instalados, 0 a remover e 15 não actualizados.
1 pacotes não totalmente instalados ou removidos.
É necessário fazer o download de 0B/4062kB de arquivos.
Depois de descompactar, 10,4MB adicionais de espaço em disco serão utilizados.
Você deseja continuar [Y/n]? 
(Lendo a base de dados ... 131807 ficheiros e directórios actualmente instalados.)
A descompactar helix-player (desde .../helix-player_1.0.6-3_i386.deb) ...
dpkg: erro processando /var/cache/apt/archives/helix-player_1.0.6-3_i386.deb (--unpack):
 a tentar sobre-escrever `/usr/share/locale/de/LC_MESSAGES/libgtkhx.mo', que também está no pacote realplay
dpkg-deb: subprocesso paste morto pelo sinal (Pipe quebrado)
Foram encontrados erros enquanto processava:
 /var/cache/apt/archives/helix-player_1.0.6-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


need some help how to resolve this...
Sup3Roque

---

### Post by Damanther on 2007-08-19
Looks like it is complaining about realplay.( Limited Spanish )
You might try reinstalling that with apt-get instead of automatix.

Or use the gui update manager, or even synaptic package manager to install the packages you are looking for. They are a little easier to navigate.

---

### Post by Jimmyfj on 2007-08-19
With my absolutely no good spanish it seems that you have a damaged packet on your system - Try Synaptic, Look for the tab Filters at the lower left site of the screen - Click on the tekst saying Damaged this will show is there's damaged packets  on your system. Simply right-click on the red square and select remove. Then you can reinstall the packet if needed.

---

### Post by r4ik on 2007-08-19
They had a subforum here once it was removed by by there request.
You can find the forum here, 

[http://www.getautomatix.com/forum/](http://www.getautomatix.com/forum/)

Good luck !

---

### Post by por100pre1 on 2007-08-19
Try removing Helix Player first, that can help you somehow. By the way, that's Portuguese, not Spanish. :cool:

---

### Post by RomeReactor on 2007-08-19
Hi It's actually Brazilian Portuguese, I think. From what I could gather, first it complains of having 15 packages not upgraded, then there's this:
> dpkg: error processing /var/cache/apt/archives/helix-player_1.0.6-3_i386.deb (--unpack):
while trying to overwrite `/usr/share/locale/de/LC_MESSAGES/libgtkhx.mo' that is also in package realplay

sup3roque, you should probably remove realplayer before trying to install helix player.

EDIT: por100pre1 beat me to it.

---

### Post by sup3roque on 2007-08-19
> **Jimmyfj said:**
> With my absolutely no good spanish it seems that you have a damaged packet on your system - Try Synaptic, Look for the tab Filters at the lower left site of the screen - Click on the tekst saying Damaged this will show is there's damaged packets  on your system. Simply right-click on the red square and select remove. Then you can reinstall the packet if needed.


and yes it's Portuguese :lolflag:

Thanks to all 
u r :KS :KS :KS :KS :KS

---

