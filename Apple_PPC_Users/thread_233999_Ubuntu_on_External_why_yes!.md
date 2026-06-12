---
title: "Ubuntu on External??? why yes!"
date: 2006-08-10
forum: Apple PPC Users
---

### Post by se1zure on 2006-08-10
Hello! My name is Cory. I am interested in booting my PPC imac g4 from an external firewire hard drive. I installed ubuntu on the external drive using both the live cd, and the alternate cd. Both *Seemed* to install perfectly fine. When I restart my mac, the only way I can think to boot from the drive is to hold down the "option" key, to choose a drive to boot from. I click on teh firewire hard drive, which even has a linux penguin on it. A black screen comes up with the text along the lines of:

"
l for linux
m for mac osx
c for cd
boot:
"

When I type in "l", it takes me back to the screen where you selec tthe drive to boot from.

What can i do to boot from the external firewire hard drive... I searched for several soulutions, and found *some* things, but everything is beyond my scope as far as linux and inits and whatnot (I have no idea what an init is btw). I have used the live cd for about 2 hours, but can't put apps on. could anyone give me a dumbed down, barebone tut on how to boot into linux on a mac from an external firewire hard drive. (i've already spent like $60, $40 for the enclosure, and $20 for the 40 gig hd).

---

### Post by linear on 2006-08-10
You can find some info here: [http://macubuntu.blogspot.com/](http://macubuntu.blogspot.com/), but I won't say it's easy.

---

### Post by se1zure on 2006-08-10
Thanks for the linke, it's a little helpful, but It seems like it's impossible to talk to a linux user without them thinkging you know everything in the world... lol. The only work i've ever done is putting linux on my ipod, which was fairly easy.

1. what is yaboot.conf
2. what is a bootstrap?
3. what in the world is kernel
4. his install returned an error at the "yaboot" part, mine installed successfully.
5. what the hell does about every thrid word mean in his sentences

I looked up some of them, but the definitions are just as confusing....

Hopefully I'm not stick with this hd enclosure and drive (if this doesn't work).

---

### Post by oswaldkelso on 2006-08-11
You could try swapping out your enclosure HD into your Mac doing a clean install then swapping the HD's back. It's very quick on most mac's check here. [http://search.info.apple.com/index.html?q=replace+hard+drive+&search=Search&lr=lang_en&search=Go&type=kmanual](http://search.info.apple.com/index.html?q=replace+hard+drive+&search=Search&lr=lang_en&search=Go&type=kmanual)
Down load the pdf for your machine and print out the instructions.
I dont know if it works but its easy to try, you may need to set the "jumper" on the hard drive to the same as your mac HD (the jumper is a slide on / off metal clip that changes the state of your HD the 3 main ones are Master/Cable select/Slave) the state varies depending upon the compuer and the make of HD. I have found that the CD/DVD drive tends to be Master and the HD is CS or slave. 

Once copied place your HD back in your enclose and hopefully it will boot.

If you hang on a while I'll do a test run here to see if it works. I have to go out for 4/5 hour but I'll do it later.

---

### Post by oswaldkelso on 2006-08-11
Sorry to have to report it failed to boot on either My G4 tower or Emac. On the Tower I got a white screen with "boot-mac" or "shut down" on the Emac I got the disks showing up but after I selected it as the boot disk and got the black screen with press
L for linux
x for Osx
C for CD

options it just booted into My usual ubuntu desktop. I have no idea if it would have booted of the exteral HD if I had not had Linux already on My Mac.

---

### Post by linear on 2006-08-11
se1zure, the main problem is that booting from an external firewire disk is not supported (the code is just not there), hence the need for scary-sounding patches. Basscakes explained the background in the post [here]("http://en.wikipedia.org/wiki/Kernel_%28computer_science%29"). You have a steep learning curve ahead if you decide to go through with this.

(Just remember that the forum search, the [Ubuntu wiki]("http://wiki.ubuntu.com/"), and Google are your friends.)

---

### Post by tidris on 2006-08-11
> **linear said:**
> se1zure, the main problem is that booting from an external firewire disk is not supported (the code is just not there), hence the need for scary-sounding patches. Basscakes explained the background in the post [here]("http://en.wikipedia.org/wiki/Kernel_%28computer_science%29"). You have a steep learning curve ahead if you decide to go through with this.

(Just remember that the forum search, the [Ubuntu wiki]("http://wiki.ubuntu.com/"), and Google are your friends.)

So what would it take to convince the Ubuntu developers that support for booting from firewire should be in the kernel by default?

---

### Post by Synchro on 2006-08-17
No idea - this question has been asked about once a week for the last couple of years. Since it's extremely likely that Mac users in particular will want to do this (For MacMini servers it's almost a requirement), it's denying Ubuntu to them almost entirely. It's been complicated further by Intel Macs as they use a completely different way of booting that's nothing like the PPC machines, so firewire hacks that work for PPC (like the macubuntu link above) will not work on current machines. Putting the hard drive in a different machine won't help either - it's not installing that's the problem, it's booting. You also described regular IDE drives, which Apple has not used for a while - it's all SATA now.
All this compiz/xgl stuff that's getting so much attention is completely irrelevant if you can't boot.

---

### Post by mokelvey on 2006-08-20
I'm trying to install ubuntu Dapper Drake build onto a buss-powered Firewire drive through a 17" G4PPC aluminum for logical reasons - I don't want to mess with the OS X installation and files. Dapper boots to its RAMdisc just fine and all the apps run except the install app stalls at about 15% along the way - not enough to do anything I know how to do with the terminal. Therefore I cannot INSTALL to an external Firewire Disk, much less boot from it. 

If there are any folks out there who have the patience to explain how this can be done, there are many of us MacWimps who would appreciate it. 

We have had to run Virtual PC whle on the road since Connectix - I never tried the MS version - but it is slow slow slow. 

Now we have all the PC programs at the office running on our MacTel Mini, even including the PC only Ricoh scanner and all the specialized PC database programs we need. But this Linux is a tuff nut to crack.

thanks - mok

---

