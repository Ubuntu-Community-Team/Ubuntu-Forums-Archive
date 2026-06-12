---
title: "Virtualbox error with synaptic"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2007-04-24
I am getting this error when trying to run updates or synaptic.  I can't enter synaptice.  I uninstalled virtual box with automatix 2 and it shows uninstalled.  Now I can't get automatix to load it either.  I am not sure how to reinstall it and not get this error.  I even tried the .deb package on virtalbox website.

this is the error I am getting.



E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.


any help would be appreciated.

---

### Post by Jazztux on 2007-04-25
Hi,
though I have never seen this error, I'll try to help you. First of all, open the console (gnome-terminal in GNOME or konsole in KDE). 
Now type:

```
sudo bash
```

to get root privileges. With apt-get, let's try to remove the old package if it's not:

```
apt-get -f remove virutalbox
```

after a few lines like the following ones (you see, I'm Italian), apt will ask you if you want to continue:

```

root@XXXXXXXXX:~# apt-get -f remove virtualbox
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso       
Lettura delle informazioni di stato in corso... Fatto
I seguenti pacchetti sono stati installati automaticamente in precedenza e ora non sono più necessari:
  libwxgtk2.6-0 libwavpack0 libjaxp1.2-java-gcj libwxbase2.6-0
Usare "apt-get autoremove" per rimuoverli.
I seguenti pacchetti saranno RIMOSSI:
  virtualbox
0 aggiornati, 0 installati, 1 da rimuovere e 3 non aggiornati.
È necessario prendere 0B di archivi. 
Dopo l'estrazione, verranno liberati 23,4MB di spazio su disco.
Continuare [S/n]?
```

so say 'Y' and press <ENTER> to agree.  If there won't be any error, you had removed the old and corrupted virtualbox package. Now we can reinstall the virtualbox package. We first have to install a GNOME util (if you use KDE it's not a problem) typing:

```
apt-get install gdebi
```

Now we will download the virtualbox package. To download the Edgy version (to change the version replace 'edgy' with you distro name such as 'dapper' or 'feisty') type:

```

wget http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_edgy_i386.deb
```

and now we do the trick:

```
gdebi (then type 'V' and press the <Tab> key)
```

and when it asks to you, accept to install paqckage and you've done.
Then try to use virtualbox and to open synaptic. Does all the stuff work? To remove the packagage file you've downloaded (it is no longer useful) type:

```
rm (then type 'V' and press the <Tab> key)
```

Let me know if it works. Bye

---

### Post by gentlemanmasher on 2007-04-25
I get this error when I try to remove virtualbox.

root@caippers-desktop:~# apt-get -f remove virutalbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
root@caippers-desktop:~#

---

### Post by compiledkernel on 2007-04-25
Im not sure what A-X would have done to cause this , but you might want to refer back to them at [http://www.getautomatix.com](http://www.getautomatix.com) to get your issues resolved from that side. 

As always I caution the use of 3rd party software like AX (Or easyubuntu as well). 

Try this -- 

[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

---

