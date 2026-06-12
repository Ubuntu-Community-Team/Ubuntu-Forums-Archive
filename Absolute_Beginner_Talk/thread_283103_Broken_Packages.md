---
title: "Broken Packages"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by Sarah13 on 2006-10-23
Hello all! While I've been trying to get my flash to work (see [this thread]("http://www.ubuntuforums.org/showthread.php?t=282610")), I have run into a problem with Easy Ubuntu. I downloaded it and installed it, but when I open it up to install the codecs, etc, it shows me the progress bar, then this error:

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

Then I receive another pop up message stating:

Could not apply changes! Fix broken packages first!

How do I fix this?

---

### Post by fatsheep on 2006-10-23
There's information on adding keys here:

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by bulldog on 2006-10-23
In synaptic the second tab repare broken packages.

And give automatix a try.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by Sarah13 on 2006-10-23
> **bulldog said:**
> In synaptic the second tab repare broken packages.

And give automatix a try.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Ok. I didn't know it could repair broken packages, so I just tried it and it says that it's not available. I'm wondering if, since it's already installed and won't repair, obviously doesn't work, should I just completely remove it then reinstall it?

---

### Post by bulldog on 2006-10-23
> **Sarah13 said:**
> Ok. I didn't know it could repair broken packages, so I just tried it and it says that it's not available. I'm wondering if, since it's already installed and won't repair, obviously doesn't work, should I just completely remove it then reinstall it?

You misunderstood me,you should repair your broken packages first with synaptic.

After that install automatix2 and you can install a lot of software like flash-player and java and a lot more.:D

Don't remove synaptic please,you'll be sorry if you do.

---

### Post by Sarah13 on 2006-10-23
> **bulldog said:**
> You misunderstood me,you should repair your broken packages first with synaptic.

After that install automatix2 and you can install a lot of software like flash-player and java and a lot more.:D

Don't remove synaptic please,you'll be sorry if you do.


Oh. That's not what I meant, I would never uninstall synaptic, I can tell it will definitely be worth its weight in gold. What I meant was that should I completely remove flash then install it again for a clean start? 

So do you prefer automatix2 over EasyUbuntu? If so, how do I uninstall it? From the Add/Remove option on Applications?

Then, if I use automatix2, I edit my sources list by entering ```
sudo gedit /etc/apt/sources.list  in terminal
```?

They say to substitute 'gedit' with the text editor of my choosing, if I want to use just the basic Text Editor, do I have to change anything?

Then, if I understand this correctly, I add ```
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
``` to my sources list. Does the order matter or can I just put it anywhere in the sources list?

Then I save the file and close it.

Then enter this in terminal:

```
wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
 gpg --import key.gpg.asc
 gpg --export --armor 521A9C7C | sudo apt-key add -
```

Then wait until that is done and enter this code:

```
sudo apt-get update
sudo apt-get install automatix2

```

Does that sound correct?

---

### Post by Synikk on 2006-10-23
You should be able to remove EasyUbuntu with Synaptic, but you should able to just use
```
sudo apt-get remove easyubuntu
```
to uninstall it.

I've never used Automatix or EasyUbuntu, since I prefer to install things manually, but Automatix seems a lot more popular than EasyUbuntu.

"gedit" is the basic text editor in Ubuntu. It's just called "Text Editor" in the menus for simplicity's sake. However, whenever you open it from the command line, you have to use its actual package name, which is "gedit."

For lots of info on adding repositories to your sources.list, [see this enty in the wiki]("https://help.ubuntu.com/community/Repositories/Ubuntu").

---

### Post by Sarah13 on 2006-10-24
> **Synikk said:**
> You should be able to remove EasyUbuntu with Synaptic, but you should able to just use
```
sudo apt-get remove easyubuntu
```
to uninstall it.

I've never used Automatix or EasyUbuntu, since I prefer to install things manually, but Automatix seems a lot more popular than EasyUbuntu.

"gedit" is the basic text editor in Ubuntu. It's just called "Text Editor" in the menus for simplicity's sake. However, whenever you open it from the command line, you have to use its actual package name, which is "gedit."

For lots of info on adding repositories to your sources.list, [see this enty in the wiki]("https://help.ubuntu.com/community/Repositories/Ubuntu").

Thanks! EasyUbuntu is now completely removed, and now I'll try my hand at Automatix.

---

