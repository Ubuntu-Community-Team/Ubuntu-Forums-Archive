---
title: "What did I do now?"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by maccawolf on 2007-04-01
My biggest problem is that I know enough to be dangerous. Well, maybe in Winblows, but in Linux I DON'T know enough, and I'm still dangerous.

Anyway, I'm going back and forth between manually trying to update with APT-GET and with synaptic, and apparently I've done something to cause THIS error:


NO_PUBKEY 2EBC26B60C5A2783

WHat did I do? and how do I fix that? I've tried everything I could find that I thought I changed, and changed it all back. (or so I thought)](*,)

---

### Post by overdrank on 2007-04-01
> **maccawolf said:**
> My biggest problem is that I know enough to be dangerous. Well, maybe in Winblows, but in Linux I DON'T know enough, and I'm still dangerous.

Anyway, I'm going back and forth between manually trying to update with APT-GET and with synaptic, and apparently I've done something to cause THIS error:


NO_PUBKEY 2EBC26B60C5A2783

WHat did I do? and how do I fix that? I've tried everything I could find that I thought I changed, and changed it all back. (or so I thought)](*,)

Hi, I believe you did nothing wrong its just the program you are trying to update, you have not added the public key.

---

### Post by maccawolf on 2007-04-01
OK, so I didn't BREAK anything, but do I want to add the public key? and if so, how do I do that? If not, how do I get rid of the error?
It would drive me absolutely batty if I had to live with that error popping up for the rest of my Ubutu life...

---

### Post by overdrank on 2007-04-01
> **maccawolf said:**
> OK, so I didn't BREAK anything, but do I want to add the public key? and if so, how do I do that? If not, how do I get rid of the error?
It would drive me absolutely batty if I had to live with that error popping up for the rest of my Ubutu life...

Well did you add any additional software repose to you installation, if you did simply remove or find and add the the key.:)

---

### Post by rillip on 2007-04-01
I think to get a better answer, you're going to need to tell us a) what is giving you the error b) what you've been trying to do.

The only use of pbulic key I'm aware of is for encryption, and that's usually for SSH.  If you're not using SSH, I don't see where that error will make one lick of difference, but then again I don't know how you'd be seeing it if it's not something you're doing! So, please fill us in with some details and I'm sure some one will be able to tell you a) why it happened b) what to do next.

---

### Post by maccawolf on 2007-04-01
I get the error at the end of sudo apt-get update AND if I reload in synaptic package manager.

WHy am I doing those things? I don't know, I guess I'm just trying to make sure I have everything I need in my system. Ultimately, I'm trying to get rid of a gnome settings error when I boot.

I guess the point is that I REALLY DON'T know what I'm doing. THa's probably most of the problem right there...LOL

---

### Post by rillip on 2007-04-01
:shock:  Ugh... interesting error.... not really sure on that one, need somebody with more experience on this one.  Good luck!!

---

### Post by chewearn on 2007-04-01
First of all, when you get the error, the error message should tells you which repository is the culprit.  (for example [http://archive.ubuntu.com/ubuntu/)]("http://archive.ubuntu.com/ubuntu/%29").

Then, you make sure the repository is a valid one i.e. you are trusting the source.   With the example above, ubuntu.com is definitely something you can trust (else why are we installing ubuntu? :))

Then, you get the public key by running these lines in terminal:
```
gpg --keyserver hkp://subkeys.pgp.net --recv-key *<2nd-half of key>*
``````
gpg --export --armor *<2nd-half of key>* | sudo apt-key add -
```Replace *<2nd-half of key>* with the actual "second half" of key.  Example, for the key from post #1: 2EBC26B60C5A2783 you replace *<2nd-half of key> *with 60C5A2783

Now, if the repository is not one you know, then edit your sources.lst and remove it.

---

### Post by Rui Pais on 2007-04-01
> **maccawolf said:**
> ...
 guess the point is that I REALLY DON'T know what I'm doing. THa's probably most of the problem right there...LOL

you add a repo to your source list but you don't give the public key.

What have you manually put in your /etc/apt/sources.list?

Do you mind to post the file?

---

### Post by maccawolf on 2007-04-02
Rui Pais,
 I had (I've now re-installed Ubuntu, last night, and the only thing I have loaded so far is the key to turboprint and Adobe from Add/remove.) tried to install Wine and screwed that up cos it was 5:30 AM, and I have since learned never to )(*&+)*+_)_around with loading stuff at that hour.

ANyway, I have been experiencing this repository problem on and off for the whole 3 weeks I had Ubuntu installed. I finally (Friday) installed the replacement repository list from the wiki page.

---

### Post by SaddaGocaraRupa on 2007-04-02
i'm getting a similar error...it's coming from the screenlets repository, which i think is trusty enough :)

```
W: GPG error: http://hendrik.kaju.pri.ee edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CDFC261E619A3D4E
W: You may want to run apt-get update to correct these problems

```

...

so i ran hastalavista's terminal lines...the first one went fine, then on the second one, it gave me an error message (key not found), so i ran another update and it gave me a different pubkey. so i ran it again with the new key and received:

```
W: GPG error: http://hendrik.kaju.pri.ee edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CDFC261E619A3D4E
W: You may want to run apt-get update to correct these problems
gg@gg-laptop:~$ gpg --export --armor  CDFC261E619A3D4E | sudo apt-key add 
gpg: can't open `': No such file or directory
gpg: [stdout]: write error: Broken pipe
gpg: iobuf_flush failed on close: file write error
gg@gg-laptop:~$ 


```

---

### Post by zvacet on 2007-04-02
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -[/B]

gpg --keyserver hkp://subkeys.pgp.net --recv-keys CDFC261E619A3D4E
 gpg --export --armor CDFC261E619A3D4E  | sudo apt-key add -

---

### Post by SaddaGocaraRupa on 2007-04-02
> **zvacet said:**
> [B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -[/B]

gpg --keyserver hkp://subkeys.pgp.net --recv-keys CDFC261E619A3D4E
 gpg --export --armor CDFC261E619A3D4E  | sudo apt-key add -

fixed! thank you very much!
:guitar:

---

