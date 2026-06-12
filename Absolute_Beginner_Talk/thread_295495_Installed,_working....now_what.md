---
title: "Installed, working....now what?"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by Bazzaah on 2006-11-08
I've finally got Ubuntu set up and it's all working just fine. I'm writing this from Ubuntu in fact.

I have a couple of questions though. I think I've managed to install drivers for my ATI card - the resolution changed after an install I did following another thread on this board. Is there a way I can check though, something like an equivalent of dxdiag in Windows?

I also installed some codecs via EasyUbuntu but still don't seem to be able to play DVDs on Ubuntu. Not a serious problem but would be nice to be able to use that function sometimes. Same with Real Player10 - got that in last night but still it won't play audio or video from the BBC website.

A bit of a mixed bag but would be grateful for any help.

Thanks in advance

---

### Post by Sef on 2006-11-08
> And one last question - where do I get Synaptic from and more particularly what version should I install?


Synaptic should be installed with Ubuntu:  System > Administration > Synaptic Package Manager

---

### Post by Bazzaah on 2006-11-08
> **Sef said:**
> Synaptic should be installed with Ubuntu:  System > Administration > Synaptic Package Manager

Yes it was, was looking around last night, couldn't find but just did, so edited my post but you beat me to it! :D

---

### Post by rlozano on 2006-11-08
> **Bazzaah said:**
> I've finally got Ubuntu set up and it's all working just fine. I'm writing this from Ubuntu in fact.

I have a couple of questions though. I think I've managed to install drivers for my ATI card - the resolution changed after an install I did following another thread on this board. Is there a way I can check though, something like an equivalent of dxdiag in Windows?

I also installed some codecs via EasyUbuntu but still don't seem to be able to play DVDs on Ubuntu. Not a serious problem but would be nice to be able to use that function sometimes. Same with Real Player10 - got that in last night but still it won't play audio or video from the BBC website.

A bit of a mixed bag but would be grateful for any help.

Thanks in advance

for ati, are you using the fglrx driver? if you are you can try fglrxinfo or glxinfo | grep rendering (u should get a yes answer if its enbaled) and you can run glxgears to see if you have a good rate of fps.

gor your multimedia requirement, im not sure if you are using Dapper or edgy, but i suggest you use automatix2 for those requirements. easyubuntu is just not working well with edgy atm.

to play those video in the websites, you might need to install the flash-plugins. you may have version 7 plugin and the site you are visiting is using a flash version 9. u can get version 9 from adobe site and download the plugin for debian.

hope this helps.

---

### Post by Bazzaah on 2006-11-08
Thanks will check those suggestions out.

In the meantime, I just tried to update Synaptic and got the following error message - do you know how I can remedy this?

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

---

### Post by rlozano on 2006-11-08
you may want to try to enable your multiverse and universe software sources.

---

### Post by Bazzaah on 2006-11-08
verified that drivers are installed, so thanks for that.

the error I report above prevents automatix2 from installing. Would really appreciate some help with that.

Thanks!

---

### Post by sKuarecircle on 2006-11-08
I had the same problem viewing video off a webpage, you need to install Automatix and then install the non-free codecs, sorted it out for me. now as for as multimedia is concerned there is no difference between windows and linux. can't view flash stuff though.Though I haven't even tried to fix that problem yet.

---

### Post by Bazzaah on 2006-11-08
I would like to do that very much, but how?

---

### Post by sKuarecircle on 2006-11-08
> **Bazzaah said:**
> verified that drivers are installed, so thanks for that.

the error I report above prevents automatix2 from installing. Would really appreciate some help with that.

Thanks!

Oh sorry, wasn't aware that you had already attempted that. can't help you to be honest, hopefully someone else can shed some light

---

### Post by bluenova on 2006-11-08
> **Bazzaah said:**
> Thanks will check those suggestions out.

In the meantime, I just tried to update Synaptic and got the following error message - do you know how I can remedy this?

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
You need to run this in a terminal
```
wget http://easyubuntu.cafuego.net/969F3F57.gpg -O - | sudo apt-key add -
```

---

### Post by Bazzaah on 2006-11-08
> **bluenova said:**
> You need to run this in a terminal
```
wget http://easyubuntu.cafuego.net/969F3F57.gpg -O - | sudo apt-key add -
```

that didn't do the trick, but thanks for the suggestion.

---

### Post by Bazzaah on 2006-11-08
all sorted - figured how to enable universe Thanks to these guys.

mulitverses.[http://simplyubuntu.wordpress.com/2006/06/24/10-tips-for-the-ubuntu-newcomer/](http://simplyubuntu.wordpress.com/2006/06/24/10-tips-for-the-ubuntu-newcomer/)

Thanks for help everyone.

---

### Post by Bazzaah on 2006-11-08
Just trying to update Synaptic once again and now I get the message. 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

INterestingly I also get the same message from Automatix, which has trouble installing Debian, additional fonts and Adobe.

Synpatic then goes on to say

Could not upgrade the system!
Fix broken packages first.

Any ideas? I was chuckling away at Windows the other day as it wants to upgrade windows installer but it can't as windows installer is corrupted on my XP install. Now I seem to have a similar problem on Ubuntu.

Any ideas on what I can do to get Ubuntu to disgnose which applications or parts of Ubuntu are broken?

Thanks...

---

### Post by sKuarecircle on 2006-11-08
> **Bazzaah said:**
> Just trying to update Synaptic once again and now I get the message. 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

INterestingly I also get the same message from Automatix, which has trouble installing Debian, additional fonts and Adobe.

Synpatic then goes on to say

Could not upgrade the system!
Fix broken packages first.

Any ideas? I was chuckling away at Windows the other day as it wants to upgrade windows installer but it can't as windows installer is corrupted on my XP install. Now I seem to have a similar problem on Ubuntu.

Any ideas on what I can do to get Ubuntu to disgnose which applications or parts of Ubuntu are broken?

Thanks...

Run 'dpkg --configure -a' in a terminal, normally wprks for me, unless you have done it already, in which case back to the drawing board

---

### Post by Bazzaah on 2006-11-08
> **sKuarecircle said:**
> Run 'dpkg --configure -a' in a terminal, normally wprks for me, unless you have done it already, in which case back to the drawing board

I did and it says 'requested operation requires a superuser privilige'.

Curioser and curioser.

---

### Post by sKuarecircle on 2006-11-08
Try 

[HTML]Sudo dpkg --configure -a'[/HTML]

---

### Post by Bazzaah on 2006-11-08
that seems to have done the trick, thanks!

---

### Post by ThrobbingBrain66 on 2006-11-08
> **Bazzaah said:**
> Thanks will check those suggestions out.

In the meantime, I just tried to update Synaptic and got the following error message - do you know how I can remedy this?

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

this just means you have to get the key from the key server:

```

gpg --keyserver subkeys.pgp.net --recv KEY
gpg --export --armor KEY | sudo apt-key add -

```

be sure to replace 'KEY' with the last 8 digits of that long number ( 12B83718 )

---

### Post by Bazzaah on 2006-11-08
great thanks - using that key and the commands you suggest has sorted that one last issue out!

Thanks!

---

### Post by guilag on 2006-11-08
> W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

When a repository in this list has a GPG key, you may need to add that to the APT trusted keys. You can do this with the following commands (replace KEY with the key ID)

>       gpg --keyserver subkeys.pgp.net --recv KEY
      gpg --export --armor KEY | sudo apt-key add -

---

### Post by sKuarecircle on 2006-11-08
> **Bazzaah said:**
> that seems to have done the trick, thanks!

Well as we would say in the land of rugby, braaivlies, sunny skys and chevrolet.....................................lekka

---

