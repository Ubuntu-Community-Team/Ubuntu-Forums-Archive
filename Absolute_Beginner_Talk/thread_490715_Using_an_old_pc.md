---
title: "Using an old pc"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by JohnGalt on 2007-07-02
I got an old HP pc back from a guy that was supposed to work on it. He's had it over a year and I don't think he ever touched it. I'm not sure what the original problem with it was as I wasn't in town when it screwed up. I'd had Win XP home on it before. I'm trying to get Ubuntu on it. It has a 256 mb stick of ram but bios is only calling it a 128.

When I booted it up, it came up with an improper shutdown screen. When I would press enter on any of the options it would restart the system and reappear with the improper shutdown screen again. Over and over. I put in the Ubuntu disk and pressed enter on the install option. Restarted again. Tried running from disk and it restarted again. I put in Sabayon and tried running it. Gave me a resolution error and once selected would restart again. Tried installing and same problem.

I put in the windows XP disk and reformatted the hard drive to install windows. It copies over all the windows files and when it restarted, it went through the splash screen and instantly restarted, and repeated the cycle until I booted up with xp disk.Then I tried bootcfg, fixboot, fixmbr. Nothing has helped and ubuntu still won't install.

I'm completely lost with what to do. Tried to google it but haven't come up with any help. Thanks

---

### Post by oilchangeguy on 2007-07-02
quote 
"I'm completely lost with what to do."
throw away the computer. and get something that works. and then install ubuntu on it.

---

### Post by splintercellguy on 2007-07-02
You could just wipe HDD and install Xubuntu or a lighter distro.

---

### Post by JohnGalt on 2007-07-02
Thanks. I'll send you the address so you can send me the money or the pc. Until I get one or the other, I want to know what could be the problem with this one. If it's software, bios, mbr, or hardware being fried.

---

### Post by JohnGalt on 2007-07-02
So you think it's the lack of ram that causes it to restart everytime, or lack of processing? It worked before I left but screwed up while I was gone and never got to see what originally happened to it.

---

### Post by mlentink on 2007-07-02
> **JohnGalt said:**
> It has a 256 mb stick of ram but bios is only calling it a 128.

So....
Have you done a memtest? It's on the Live CD.
If it is really only 128 megs, you're not going to run Ubuntu on it. I'd check the upgrade possibilities if I were you.


EDIT: Some more info on the system would be helpful too. Like processor, Graphics Card, harddisk size, the works...

---

### Post by reset3x on 2007-07-02
If you're saying you have a 256 meg stick installed and it's ticking off 128 at post you should try running memtest86 from one of the Live CD's... Also you should check to see what type of mem you pc supports.. ie: 32bit, 64bit etc... You could also have a bad mem controller on your mobo...

---

### Post by JohnGalt on 2007-07-02
It's reading 127 on post while the bios reads it as a 128. It's a compaq presario 5000. I'm trying to figure out what kind of ram now. Probably isn't worth while to mess with though.

---

### Post by reset3x on 2007-07-02
Maybe the guy that was "supposed" to work on it... did...

---

### Post by mlentink on 2007-07-02
:rofl:

---

### Post by JohnGalt on 2007-07-02
Sorry mlentink, it's the compaq presario 5000.
[http://www.shopping.com/xPF-Compaq-Presario-5000-470010-120](http://www.shopping.com/xPF-Compaq-Presario-5000-470010-120)

It's only capable of 512mb of ram. I'm better off getting my friends computer that just ate the dust. Make sure the powersupply is good on it and replace the mobo/proc/ram on it. At least the powersource on it was running a p4 before it fried out.

Edit: Whats the meaning of the stuff under the screen names?
On second thought, $30 for 256 so $60+ shipping might not be too bad I guess. I'd still would rather be running a gig and dual or quad core. Just got to wait for that money to be sent to me, ha

---

### Post by mlentink on 2007-07-02
Hey, 
I'm typing this on a 512 Meg Compaq Evo D300, with a 1.2Gig processor. Runs just fine, thank you.

But frankly, I think you're right about upgrading that box. Sounds like it's flakey at best...

---

### Post by oilchangeguy on 2007-07-02
> **JohnGalt said:**
> Sorry mlentink, it's the compaq presario 5000.
[http://www.shopping.com/xPF-Compaq-Presario-5000-470010-120](http://www.shopping.com/xPF-Compaq-Presario-5000-470010-120)

It's only capable of 512mb of ram. I'm better off getting my friends computer that just ate the dust. Make sure the powersupply is good on it and replace the mobo/proc/ram on it. At least the powersource on it was running a p4 before it fried out.

Edit: Whats the meaning of the stuff under the screen names?

by the time you replace the ram, mobo, and cpu, you can go but a new computer. why waste your time or money? go buy something new.

---

### Post by reset3x on 2007-07-02
> **mlentink said:**
> Hey, 
I'm typing this on a 512 Meg Compaq Evo D300, with a 1.2Gig processor. Runs just fine, thank you.

But frankly, I think you're right about upgrading that box. Sounds like it's flakey at best...

Yeah if it's ticking off 127 with 128 installed something is hosed...

You could try plucking that stick and reseating it to see if that helps... With 128 meg you'd need to run something like Puppy Linux or Damn Small Linux... Or if you get the thing working right buy more mem and run X/Ubuntu...

---

### Post by JohnGalt on 2007-07-02
I was wrong, thought it was a 256, but it is only a 128 posting at 127 on mem test.pc100-222-620.

It used to run winxp on it ok, but a lil slow. Should the hard drive be ok to pull out and use again? I know that it had been upgraded. I don't remember how big it is but no use throwing away a hard drive.

By just replacing the mobo, cpu, and ram I can save the money by not buying another case, power supply, os, sound card and video card. I can use the money I would of spent on those things to buy a better mobo,cpu, and more ram.  I have the sound card and graphics card from my computer I gave my dad for his business. His ram fried one day and needed the pc for all the buisness work. Thats why I can't  put linux on it, and now I'm out of a pc. The next time I drop money for a new computer its going to be for a laptop. I was just hoping to use this as a linux box to play with and learn about linux.

Edit: I know 512 mb is fine on a p3 1 ghz and even less if you're using a low mem os. I just like all the fancy visuals. I used Ubuntu for a short while before but got tired of dual booting to use photoshop, couldn't get wine to work and hate gimp.

I wish I had the money for this pc if I was to get a desktop. [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2205245&Sku=G153-GT5056](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2205245&Sku=G153-GT5056)

---

### Post by reset3x on 2007-07-02
> **JohnGalt said:**
> I was wrong, thought it was a 256, but it is only a 128 posting at 127 on mem test.pc100-222-620.

It used to run winxp on it ok, but a lil slow. Should the hard drive be ok to pull out and use again? I know that it had been upgraded. I don't remember how big it is but no use throwing away a hard drive.

By just replacing the mobo, cpu, and ram I can save the money by not buying another case, power supply, os, sound card and video card. I can use the money I would of spent on those things to buy a better mobo,cpu, and more ram.  I have the sound card and graphics card from my computer I gave my dad for his business. His ram fried one day and needed the pc for all the buisness work. Thats why I can't  put linux on it, and now I'm out of a pc. The next time I drop money for a new computer its going to be for a laptop. I was just hoping to use this as a linux box to play with and learn about linux.

You may not have that option... I believe that power supply may have a proprietary adapter on it... Anything else you can salvage from it is not a waste... If you want to risk a few $ and gamble on you just having a bad stick of mem go to computergeeks.com and get a couple of 128 meg sticks of pc133 mem... pc133 mem is dirt cheap nowadays...


Good Luck!!

---

### Post by JohnGalt on 2007-07-02
Is emachines power supply proprietary? that's the power supply  I would of used. But if I was to start buying components I'd be better off getting that refurb that I linked to above. 

128 mb for $11, or 256mb $34.95. I don't think it's worth it. At least not for now. Thanks

---

### Post by sourjax on 2007-07-02
Here's what did. I installed Ubuntu Server with the CD, then I:

```
sudo aptitude upadate
```

Next,

```
sudo aptitude upgrade
```

then, 

```
sudo aptitude install xorg
```

Then, 

```
sudo aptitude install ubutu-desktop
```

All this took a vvery long time but, it WORKED!

Hope this helps!;)

---

### Post by JohnGalt on 2007-07-03
The unbuntu server comes on a different iso, correct? I guess it uses less ram and hope that it doesn't cause a restart upon booting right?

I can enter into bios and it seems fine. It only reboots after a startup command has been entered whether I press enter or it times out. Does this with windows boot, ubuntu disk, and sabayon disk.

---

### Post by sourjax on 2007-07-03
> **JohnGalt said:**
> The unbuntu server comes on a different iso, correct? I guess it uses less ram and hope that it doesn't cause a restart upon booting right?

I can enter into bios and it seems fine. It only reboots after a startup command has been entered whether I press enter or it times out. Does this with windows boot, ubuntu disk, and sabayon disk.

Yes you have to download the Ubuntu "Server Edition" to do what I described...

---

### Post by xthund3rh3adx on 2007-07-03
sounds like a hardware problem. 

look at the RAM. try putting in a 128MB stick or just some random stick you may have, and see if it works.
or, your computer might have finally gave out....

in which case, I recycle old hardware, and use it to help run websites and such. so, if you plan on throwing it away, PM me, and i can give you shipping instructions :D

---

### Post by ageilers on 2007-07-03
How much could ram cost on ebay. I have bought many parts on ebay and have saved myself a ton of money upgrading old PCs. Quick here's your [[COLOR="DarkOrange"]chance[/COLOR]]("http://cgi.ebay.com/512MB-2x256MB-Micron-SDRAM-PC-Memory-PC100-222-620_W0QQitemZ160132085393QQihZ006QQcategoryZ14917QQrdZ1QQcmdZViewItem").

---

