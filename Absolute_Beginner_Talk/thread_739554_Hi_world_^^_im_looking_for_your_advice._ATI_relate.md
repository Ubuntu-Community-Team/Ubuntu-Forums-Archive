---
title: "Hi world ^^ im looking for your advice. ATI related"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by Ryuki_NdranC on 2008-03-29
First thx to all for this awesome comunity. I always wanted to change for life to linux but something allways got in the way. Well not anymore:)

I managed to install kubuntu gusty and manage to install with ndiswrapper the bcm43xx driver for my wireless card in my hp dv5224nr (weeee!)

Now im using the wiki ati instalation guide so i can have 3d acceleration and hopefuly compiz fusion in the near future.

I made a screw up and i know where i did it. I used this commands:

```
sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms

sudo sh ati-driver-installer-8-3-x86.x86_64.run --buildpkg Ubuntu/gutsy

kdesu kate /etc/default/linux-restricted-modules-common
```

i added the DISABLED_MODULES="fglrx" line.

```
sudo rm /usr/src/fglrx-kernel*.deb

```

did this but told me no file found then i did

```
sudo dpkg -i xorg-driver-fglrx_8.471-0*.deb fglrx-kernel-source_8.471-0*.deb fglrx-amdcccle_8.471-0*.deb

sudo apt-get install -f

sudo dpkg -i --force-overwrite xorg-driver-fglrx_8.471-0*.deb fglrx-kernel-source_8.471-0*.deb fglrx-amdcccle_8.471-0*.deb

```

cos i have a AMD64 2.0 Ghz, Ati radeon xpress 200m.

some how i think i screw up in that last command cos i saw an error at the very end of the feedback something like fglrx allrdy installed (srry i didnt write it down)

and here is when i major screw it when i did this

```
sudo aticonfig --initial

```

without restart :(

so i got a memory dump of somekind. i restarted and now i got a black screen.

I alrdy know how to restore the xserver but i was wondering what should i undo in this failed instalation so i can fresh try again. Maybe some other advice of somekind?:)

Im rlly appreciated by the answers and excuse my poor english >.>

---

### Post by huntwell on 2008-03-29
I am somewhat of a Noob, but I have had a lot of problems with my ATI driver as well. I have the X1150 and found that installing the latest version of Envy and choosing the manual install of the ATI 8.3 driver (which is the most current) solved my problem and I was able to run compiz-fusion without any problems. 

I made the mistake of running the 8.43 driver and got a blank white screen, but when I installed 8.3 through Envy, everything worked. You should get the latest version of Envy from the link below.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

I tried going through the process you have gone through on the wiki and found it to be problematic. I found it a much easier process to get compiz-fusion working by installing manually through Envy. 

If you try this method, let me know how things turn out.

---

### Post by Ryuki_NdranC on 2008-03-29
:O didnt notice that option. Im gonna try it. But i have 2 questions.

1. There is anything i should do to remove any wrong file or thing i did in that last failed instalation???

2. Is there any difference between using [COLOR="Red"]Envy[/COLOR] or using the manual instalation? cos apparently i has doing find till i screw up at the end i think

Thx a lot for the answer, besides we all are kinda noobs just ones more than anothers.:lolflag:

---

### Post by huntwell on 2008-03-29
Ryuki,

With regard to q#1: I wish I could help you more with suggesting what to uninstall or remove with what you have already done. Since I am still learning a lot with linux since I am a nooby, I wouldn't want to suggest anything that might make things worse. Maybe someone else can tell you what to do about that.

With regard to q#2: My apologies, I should have clarified better. If you install Envy, it gives you the option to install automatically or install manually. I went with the manual option since I wanted to make sure that I could choose the most recent ATI driver, which is 8.3. The last time I installed through the automatic option it did not install the most recent driver, that is why I opted for the manual installation. Again, if you install Envy, you should see both options in the menu. I hope this makes sense.

Sorry I couldn't help you more with undoing what you have already done through the wiki. I hope someone else can help you with that.

Best of luck.

---

### Post by Ryuki_NdranC on 2008-03-29
:) Don't worry i think i can check out the commands i did and try to use common sence. So far i know how to unwrite things i wrote in conf files. The thing i dont know is if once i restored the xserver configuration if i need to remove any fglrx from anyplace they shouldnt be.

BTW [COLOR="Red"]Envy[/COLOR] downloads on his onw the driver??? cos i alrdy downloaded one.

---

### Post by Ryuki_NdranC on 2008-03-29
Ok i tryed Envy and it didn't work. I pick install manual ATI driver. Select 8-3 and got Envy ERROR: md5 error after that asked me to auto configure the xorg.conf i pick yes. reboted and got a nice black screen and after a while a wrong resolution comand line to login. I had to reboot and do:

```
envy -t --uninstall-all
```

:confused: any advice... any anyone? it will be a big disapointment not to be able to run compiz fusion.

Apriciate your time

---

### Post by Ryuki_NdranC on 2008-03-30
Well... i tried the ati installation wiki (this time following the exact steps) and got squad. :(

Envy doesn't work eather. If anyone have been following my problem i have a

HP Pavilion dv5224nr
AMD Turion64 2.0 Ghz
ATI Radeon Xpress 200m 128mb
1 gb 2ddr ram

I don't if it has anything to do put i have activeted umd+sideport in my setup. (don't remmember the exact name... umd?).

I'm going to sleep now, but the battle is not over. If you know something or maybe pointing me to a link or even just to say that its impossible... please thanks.

---

### Post by huntwell on 2008-03-30
Ryuki,

I am sorry Envy didn't work and caused problems. It worked wonderfully for me, which is why I recommended it. I think at this point, I had better stop offering suggestions. 

I hope there is someone out there who can help you out.

---

### Post by Ub1476 on 2008-03-30
You have to remove all installed ATI drivers before you use Envy. Envy should have an option to do this, and the wiki should give some info about this too (I suggest double-check everything).

Envy will work fine, just make sure any previous driver is removed.

---

### Post by Ryuki_NdranC on 2008-03-31
Hi all ^^ sorry for not posting the outcome put i finally manage to install the ATI driver with Envy. (Weeee!) :)

I do "fglrxinfo" and got everything right and the restricted driver manager says there is a driver installed ^^

I got i question dough, after GRUB loads it takes an awefull LOT of time to load the login screen. :/ Always did since the fresh install. I thought it will fix after the ATI properly install. To be more especific, GRUB loads and after that the screens goes black (no fancy text with [OK] at the end i as recall from ubuntu 6.08), and the screen stays black for about 3 minutes before poping the KDE login screen :/

Any ideas? I recall kubuntu 6.06 to be much more faster than XP now its backwards.

I don't know if i should put this on a new post but i will try here first.

Thx for the answer and thx a lot for Envy ^^

---

