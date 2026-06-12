---
title: "How easy will it be to upgrade from 8.04 beta?"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by gyzer on 2008-04-12
I'm new to Unbuntu, and I was wanting to know if it would be a good idea for me to install 8.04 beta now, or should I wait till 8.04 is out of beta? Or should I just install the current version right now and update to 8.04 when it comes out of beta?

Is doing upgrades from one version of Ubuntu to another a good idea, or are they unreliable and fresh installs are preferred?

---

### Post by tamoneya on 2008-04-12
The upgrade process is very reliable especially if you do the upgrade after the official release date.  Personally I prefer to do a reinstall because I just spent the previous 6 months breaking my system (its just what i do) and I like to know that everything is working the way it should be. 

I am using hardy right now and am having very few problems with it.  It has gotten a lot better over the past few weeks.  If you were to upgrade now you should be all set.

---

### Post by qamelian on 2008-04-12
> **gyzer said:**
> I'm new to Unbuntu, and I was wanting to know if it would be a good idea for me to install 8.04 beta now, or should I wait till 8.04 is out of beta? Or should I just install the current version right now and update to 8.04 when it comes out of beta?

Is doing upgrades from one version of Ubuntu to another a good idea, or are they unreliable and fresh installs are preferred?
Going from beta to the full release will be automatic through the update manager. Couldn't be any easier than that!:)

---

### Post by gyzer on 2008-04-12
Wow, thanks.

I can't believe I just got 2 replies in less then 5min of posting with out anyone bashing me.

I think I'm going to like it here...

---

### Post by sports fan Matt on 2008-04-12
I had stressed for 4 days or more about it and bit the bullet and did a dist. upgrade. I couldnt be happier and im glad I trusted my gut.

---

### Post by Moop on 2008-04-12
I'd say go with 8.04 beta now and it will update to the final release version. It will be less trouble than installing 7.10 and upgrading to 8.04 in a few weeks.

---

### Post by JoshuaRL on 2008-04-12
It just depends on what you think you want to do.  Do you want to risk having a little unstable system?  (although to be fair I've heard almost completely good things about Hardy)  Or do you want it to just work and be stable?  It will give you the chance to update to Hardy in a couple weeks anyway, so the choice is really up to you.

---

### Post by HunterThomson on 2008-04-12
I am new to ubuntu too and was thinking the same thing.... I did a little too much learning by error with 7.10 so I just did a clean install of 8.04 beta a few days ago and love it. I just figured it would become the full release with updates and it seems that is how it works. I get fairly major updates everyday sometimes two updates a day. Yesterday I even got a kernel update 2.6.24-15 to 2.6.24-16. I think it is a better idea to upgrade now instead of wattling this way you can see the progress right in front of your eyes.:) If you use the "upgrade" you can even encrypt your file system!! I think this is alsom I mite install 7.10 and then use the upgrade to go back to 8.04 so I can encrypt my file system.....This will protect my compute better right? So if someone roots my box they can't install a RootKit or at lest protect agents some attacks???

---

### Post by tamoneya on 2008-04-12
im not certain what you are referencing when you say encrypt your filesystem.  While this is easily done there is no reason why you would have to upgrade from gusty to hardy.  Also encrypting your filesystem primarily prevents someone from taking your harddrives from your computer and putting them in another computer to read the data.  Once the system is booted and some has gained root access the filesystem will be decrypted.

---

### Post by noynac on 2008-04-12
Since you're new to Ubuntu (and I assume Linux), I would recommend that you install Gutsy on a non-production machine and play around with it for a few weeks. That will allow you to learn Linux and avoid the quandry of whether a problem is something you did or a result of a beta OS. Also, if you're like most new users, you'll trash a few installs and have to reinstall regardless. Then, in 12 days, you'll have sufficient knowledge to go with Hardy.

Upgrading from one version to another is not a problem IMHO. I started with Dapper and upgraded that install to Edgy, then Feisty, then Gutsy, and now to Hardy, and everything still works great. 

BTW, if you do go with Hardy right now, you should post your questions in the Hardy forum. There's a lot of experienced Hardy users there, and it'll keep the mod's happy.  

Good luck!

---

### Post by twist2b on 2008-04-12
You can update now by changing your repos making everything say hardy instead of gusty

Though just wait for a few more days, Hardy is amazing. It works extremely, way better then gusty. Just wait though, and you can update through the update manager :P

---

### Post by rdsherwood on 2008-04-12
I too would argee with noynac. I'm also a Ubuntu Newbie. I originally installed 7.10, then upgraded it to 8.04. The upgrade went fine, but then apparently in playing around with different media players, I broke something, because suddenly my machine wouldn't boot with a "Failed To Initialize HAL" error. After realizing I was in over my Newbie head, I reinstalled 7.10, and it's been running rock solid for several days now. 

I think I'm going to now take the conservative route, let Hardy Heron go out of beta for a few weeks, then I'll ugrade.

---

### Post by HunterThomson on 2008-04-12
So, encrypting the file system would still help me with the FBI and the SS.... I know there are other programs to encrypt the file system but I just figured if the ubuntu installer was doing it things would be EZ'r and I would have fewer problems. I am not dug in at all so reinstalling the OS is no problem.

---

### Post by tamoneya on 2008-04-12
> **HunterThomson said:**
> So, encrypting the file system would still help me with the FBI and the SS.... I know there are other programs to encrypt the file system but I just figured if the ubuntu installer was doing it things would be EZ'r and I would have fewer problems. I am not dug in at all so reinstalling the OS is no problem.
 Yes it would but if this is your worry i would recommend truecrypt instead.  It will allow you to encrypt just a section of your partition and you can keep your sensitive files in there.  This is better than encrypting the entire thing because if something gets messed up with the encryption keys your computer wont boot.  Truecrypt is in the repositories and can be installed with ```
sudo apt-get install truecrypt
```

---

### Post by HunterThomson on 2008-04-12
owe ya I have truecrypt. I just want to go all out with it... for fun more then anything. But, you never know when a program will be made illegal. In some countries nmap and truecrypt are illegal. DVD decrypting programs are illegal here.

---

