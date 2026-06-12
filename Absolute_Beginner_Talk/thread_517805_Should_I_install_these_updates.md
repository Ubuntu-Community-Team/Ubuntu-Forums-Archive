---
title: "Should I install these updates?"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by szaemon on 2007-08-05
My Update Manager wants to install these and I would normally just click OK, but the warning tells me that they aren't able to authenticate them. Does anyone know what they are or if they are safe?   I'm NOT computer savvy, so I really have no idea.

libavcodec0d
libavformat0d
ffmpeg
libpostproc0d

...Then it reads:

To be upraded

ffmpeg
libavcodec0d
libavformat0d
libpostproc0d

Any information will be appreciated.
Thanks!

---

### Post by superstylin on 2007-08-05
They should... be fine... I would wait till someone with more knowledge says Yes! :)

:guitar:

---

### Post by eentonig on 2007-08-05
Did you enable extra repositories? 
Others then the provided universe/multiverse? 
And do you trust those repositories?

If the answer is "No, No, Not applicable", go on and install.
If the answer is "Yes, yes, yes", go on and install.
If the answer is "Yes, Yes, I don't know." Try to found out if they are trustworthy.

---

### Post by nitro_n2o on 2007-08-05
can't bu authenticated is not very serious most of the time.. this happens when you use packages developed by people other than ubuntu.. 
I don't know why r do u need these.. but most of the time updates are good.. if you are so worried search each package in google.. go to its website and know what is new in it.. maybe it contains some serious security update that you shouldn't miss or maybe the new changes will not work with some other software you are using for something serious... 
but don't worry too much Synaptic is your friend.. 
if you are really worried wait a little bit and if there is anything wrong with these package i'm sure that one of the debian/ubuntu guys will find about it and fix it (lovely open source) :)

---

### Post by waterman on 2007-08-05
Hi I have install Compiz Fusion and update manage wants to install compiz, compiz-core, compiz-gnome and compiz-plugins... How can I delete it from update manager??

---

### Post by esc1 on 2007-08-05
I'm not sure, but I just removed them completely from Synaptic hours ago and I'm not getting prompted for them.

---

### Post by nitro_n2o on 2007-08-05
> **waterman said:**
> Hi I have install Compiz Fusion and update manage wants to install compiz, compiz-core, compiz-gnome and compiz-plugins... How can I delete it from update manager??
I don't use compiz but i think those packages are needed in order for compiz to work

---

### Post by szaemon on 2007-08-05
Thanks for the advice. I pretty much drive with my eyes closed as far as this stuff goes. I'm trying to edit my Geocities website and it said I needed a Java Plugin to do so. The plugin won't install directly from the site, my search lead me to the Mediubuntu repository, which didn't install properly because I needed a Public Key. While trying to find/get the public key my update manager told me to install these Unauthenticatable updates, then told me doing so could let someone else hijack my system. So now I guess I'll go ahead and install them.
Thanks Again Ubuntu Community!

---

### Post by atomkarinca on 2007-08-05
> **waterman said:**
> Hi I have install Compiz Fusion and update manage wants to install compiz, compiz-core, compiz-gnome and compiz-plugins... How can I delete it from update manager??

system > administration > software sources > third party software tab. uncheck the ones that say "eyecandy" at the end (most probably you have two). then click on the updates icon and make a check. the compiz-related packages will be removed from the update list.

---

### Post by waterman on 2007-08-05
but dont that remove compiz + compiz fusion updates?? I want remove only compiz updates, no compiz fusion

---

### Post by ThrobbingBrain66 on 2007-08-05
> **waterman said:**
> but dont that remove compiz + compiz fusion updates?? I want remove only compiz updates, no compiz fusion

If you don't want to recieve compiz updates, then you have to 'lock' the packages.

In Synaptic, highlight the packages you want to lock and then in the menubar click Package > Lock package.  I think you can do a bunch at a time, but you may have to do them individually.

BTW, it's bad practice to hijack another's thread :)

---

### Post by ThrobbingBrain66 on 2007-08-05
> **eentonig said:**
> Did you enable extra repositories? 
Others then the provided universe/multiverse? 
And do you trust those repositories?

If the answer is "No, No, Not applicable", go on and install.
If the answer is "Yes, yes, yes", go on and install.
If the answer is "Yes, Yes, I don't know." Try to found out if they are trustworthy.

To add to eetonig's answer, if you did enable a third-party repo, you may want to search for a gpg key to validate the repo.  This way you won't get this message again.

[thinking out loud]
Could be the Medibuntu repo...
[/thinking out loud]

---

