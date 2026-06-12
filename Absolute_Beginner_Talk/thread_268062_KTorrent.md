---
title: "KTorrent"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by marmilho on 2006-09-29
Hey I cant use Ktorrent properly.
I've set up the port to 6884.

I'm trying to download a torrent full of peers but KTorrent doesnt download/upload at all (sometimes starts really slowy and then stops again)


Also, kinda offtopic:
How do I download Vid Codecs? I've been trying to play a clouple movies with no sucess(they are encoded in Xvid)
And Were to download a Player with subtittle support?

---

### Post by mark_g on 2006-09-29
Could you tell us more about the setup of your network? 
Do you use a router or a proxy server?

---

### Post by nudnik on 2006-09-29
> **marmilho said:**
> Hey I cant use Ktorrent properly.
I've set up the port to 6884.

I'm trying to download a torrent full of peers but KTorrent doesnt download/upload at all (sometimes starts really slowy and then stops again)


Also, kinda offtopic:
How do I download Vid Codecs? I've been trying to play a clouple movies with no sucess(they are encoded in Xvid)
And Were to download a Player with subtittle support?

Ktorrent never works properly...try Bittornado:mrgreen: 

As for video, see here

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Player with subtitle support, VLC, install thusly;

open terminal and type

sudo apt-get install vlc

---

### Post by marmilho on 2006-09-29
pppOe connection.. Used to work just fine on windows.

I had to config it with sudo pppoeconf..

I was using KTorrent cuz its the only one in Ubuntu. I wish I could install Azureus from the repositories but it aint there...
But if i'm getting trouble with KT I might get trouble with azureus aswell..



About VLC.. I got 'unable to find vlc packet(or something like that)
Gonna check out this guide.
But is Ubuntu able to run DVix and Xvid and such?


Btw thanks for the help guys

---

### Post by nudnik on 2006-09-29
> **marmilho said:**
> pppOe connection.. Used to work just fine on windows.

I had to config it with sudo pppoeconf..

I was using KTorrent cuz its the only one in Ubuntu. I wish I could install Azureus from the repositories but it aint there...
But if i'm getting trouble with KT I might get trouble with azureus aswell..



About VLC.. I got 'unable to find vlc packet(or something like that)
Gonna check out this guide.
But is Ubuntu able to run DVix and Xvid and such?


Btw thanks for the help guys

Are you using Ubuntu or Kubuntu?

Ktorrent is far from the only bittorrent client available for Ubuntu. Bittornado is in the repositories. VLC is in the repositories as well, and should install if you type the follwing exactly as it is represented below. Remember, Linux is case sensative when using the command line.

sudo apt-get install vlc

And yes, Ubuntu will play any mpeg-4 stream that I know of. (xvid, divx etc)

You may need to enable multiverse and universe repositories using synaptic. That is likely why you dont see all the packages.

---

### Post by marmilho on 2006-09-29
I need command lines to do that? I've tried looking in the GUI but could not find anything related to it.. (well mine Ubuntu is in portuguese.. So its possible I didnt recognized it.. altho I dont believe that X) )



And check this out: > milho@comp:~$ sudo apt-get install vlc
Password:
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
E: Impossível achar pacote vlc
milho@comp:~$ sudo -i
root@comp:~# sudo apt-get install vlc
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vlc



Oh well..
Anyways, how do I install Azureus by apt-get? And how to search apt-get packages via commands? I remember doing this the first time I used linux..

Yet, last answer: How to check if the port I configured the Torrent client is Open/Close/whatever?

Thanks again

---

### Post by nudnik on 2006-09-29
> **marmilho said:**
> I need command lines to do that? I've tried looking in the GUI but could not find anything related to it.. (well mine Ubuntu is in portuguese.. So its possible I didnt recognized it.. altho I dont believe that X) )



And check this out: 


Oh well..
Anyways, how do I install Azureus by apt-get? And how to search apt-get packages via commands? I remember doing this the first time I used linux..

Yet, last answer: How to check if the port I configured the Torrent client is Open/Close/whatever?

Thanks again

On the desktop, click on System>Administration> Synaptic Package Manager
Once the package manager is open, click on Settings>Repositories
Another window will open, make sure the Universe, and Multiverse options are selected. This will allow you access to all of the software, including VLC and Azureus.

Unless you have a firewall installed, the ports should be open on the PC.
How to check your router differs from one manufacturer to the next, so you would need to post that data in order for someone familiar with the unit to instruct you.

---

### Post by marmilho on 2006-09-29
Oh. They were channels.. I thought they were mere options..

Well I selected them all.

Thanks a lot man.

---

