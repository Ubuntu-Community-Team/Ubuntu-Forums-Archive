---
title: "Anyone can change my root or user password?"
date: 2005-08-07
forum: Absolute Beginner Talk
---

### Post by coolblue on 2005-08-07
From what I know, theres a way to change/reset root password & user passwords if u forget them.
 
Which means anyone having such knowhow & physical access to my PC can tamper with my linux system!
 
Is there ANY way to prevent all this?

And I really can't afford to lock up my pc....my family uses it and I'm just a 21-yr kid using the same pc:)
 
So I know that NO ONE in my family would do any intentional damage to my pc......what I ONLY want is that no one should get access to my linux system by changing password etc.
 
Apart from encrypting personal files, isn't there ANY other way? 
 
 Thanks

---

### Post by cwaldbieser on 2005-08-07
If someone has the knowhow and physical access to the machine, there is nothing you can do to stop them from gaining access to your files.  You can only make it harder for them.  You can actually do the same thing on Windows.  Not sure about Macs, but you can always just load up a LiveCD on one of them and have access to the files anyway.


Since it is your family, and there is presumably a certain amount of trust, you should just let them know that you expect them to respect your privacy and visa-versa.  

Short of that, encryption is probably your best bet if you have nosey, computer genius siblings.

---

### Post by poofyhairguy on 2005-08-07
[QUOTE=coolblue]
And I really can't afford to lock up my pc...[/QUOTE]

Hmm....Here is what I would do if you are really paranoid. 

I would enable the root password:

[http://ubuntuguide.org/#setchangeenablerootpassword](http://ubuntuguide.org/#setchangeenablerootpassword)

And uninstall sudo (or better yet, make sure no one is in the suders file:)

[http://ubuntuguide.org/#allowmoresudoers](http://ubuntuguide.org/#allowmoresudoers)

Then NEVER give out the root password. It will be a medium pain in the ass (seeing as how synaptic and many other GUI tools us sudo) but it would do the trick.

The real question is: is anyone that will touch that computer nerdy enough to learn how to reset your passowrd anyway?

---

### Post by Sam on 2005-08-07
If somebody has physical access to the machine, the best way is to make the hd the default boot device in the bios, enable the bios administration password to prevent changing the boot order to run a live cd with root access on your drives, enabling the grub password, and make sure that your password is not easy to guess.

After that, the way to access your filesystem would be to take the hard drives to install them to an another box...

More infos [here](http://ubuntuguide.org/#security).

---

