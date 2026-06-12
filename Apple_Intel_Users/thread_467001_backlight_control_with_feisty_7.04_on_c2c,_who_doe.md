---
title: "backlight control with feisty 7.04 on c2c, who does??"
date: 2007-06-07
forum: Apple Intel Users
---

### Post by kzm. on 2007-06-07
can anybody confirm that his/her backlight control is working on a macbook c2c with feisty 7.04? 
mine is not even though in the docs it says it should i also cant install the backlight package from desrt nor from nicolas (boichat).
i have no idea whats going on... hm.

---

### Post by ronocdh on 2007-06-07
> **kzm. said:**
> can anybody confirm that his/her backlight control is working on a macbook c2c with feisty 7.04? 
mine is not even though in the docs it says it should i also cant install the backlight package from desrt nor from nicolas (boichat).
i have no idea whats going on... hm.
Mine works. Given that I have a MBP, maybe it's a different case, but FWIW, mine worked OOB. MacBook users?

---

### Post by ivesjd on 2007-06-07
I'm on a core duo and it worked out of the box, just wish it would go all the way black like OS X. But oh well, it works thats all that really matters.

---

### Post by ronocdh on 2007-06-07
> **ivesjd said:**
> I'm on a core duo and it worked out of the box, just wish it would go all the way black like OS X. But oh well, it works thats all that really matters.
Yes, I find this also curious that it only goes to "dark" rather than "off." And just because, have you ever noticed that the "off" setting in OS X isn't really off? Like you can still see your cursor moving around really faintly? I dig that.

---

### Post by ivesjd on 2007-06-07
Ya, but from what I've witnessed, OS X is the only OS that does that. Which sucks because it is a very nice feature. I wonder how hard it would be change that in Ubuntu?

---

### Post by Movi on 2007-06-07
There was a regression in HAL, someone should post a bug report (maybe i will tonight). This only affects Macbooks (not Pro) Core 2 Duo. The fix is this. With admin rights, edit /usr/share/hal/fdi/policy/10osvendor/10-macbook-backlight.fdi. 
Here's the line you need to change:

<match key="smbios.system.product" string="MacBook1,1"> (this means that only Core Duo Macbooks)

change it to 

<match key="smbios.system.product" string="MacBook2,1"> (this means only Core 2 Duo Macbooks)

I noticed that a fresh install of Ubuntu _does_ work.

On a different note : suspend dies a painfull death with the newest 2.6.20-16 kernel. Someone should fill a bug too.

Edit : Oh, and don't bother installing pommed or stuff like that, it's just useless duplication of function. Stick with HAL - it's the proper way.

Edit2 : I noticed that the ubuntu release of Hal is ok, it's the backport package that broke - im trying to find means to post the bug now. Patch is on the way too as soon as i know how to patch it correctly :)

Edit3 : Bug is in launchpad now : [https://bugs.launchpad.net/feisty-backports/+bug/119184]("https://bugs.launchpad.net/feisty-backports/+bug/119184")

---

### Post by kzm. on 2007-06-09
hey "Movi" 

thanx for your comment. i will try your fix any second (have to reboot, as my wireless is stiull not working).
my suspend was working just fine. even i could in the meanwhile boot osx turn that off and go back to where i wa in ubuntu :)

you are talking about not installing pommed and others.. what does this include? does this include gsynaptic?
could you, may be for idiots like me, explain what hal is for and what you shouldnt install and how you can approach the same via hal?

---

### Post by ivesjd on 2007-06-09
Movi
I haven't had any problems with suspend **knocks on wood** Is that only for C2D's or what? 
kzm
Your saying that you can suspend Ubuntu, and then shut the computer off, boot to OS X and then boot your Ubuntu session again? If it is suspend to RAM then that is impossible. Unless it suspends to swap or disk. I would be interested to know exactly what you are doing though. :)

---

### Post by Movi on 2007-06-10
In pommed i mean programs that take control of your "feature keys" like the volume up-down keys, the brightness keys and the eject key. syndaemon has nothing to do with it (though i would like HAL to take care of touchpads too :) )

Edit : I just updated to the newest kernel - 2.6.20-16.29 and my MacBook suspends again! :)

Also, i just tried Gutsy Tribe 1 : the macbook-backlight bug is still there, the fdi file is wrong in the same way as i wrote above. Can someone XML-knowledgable write a patch that would include _both_ Macbook1,1 and Macbook2,1 so that i can send it upstream for inclusion?

---

### Post by kzm. on 2007-06-11
true.. after i posted this, i was eating and thinking "something is wrong in what you said" .
anyway.. suspend to ram works fine with me.. i just tried it again, to make sure i am not bullshitting again.

when i opened the *.fdi i got this! this cant be right, or is it just me? i didnt put this there (at least not by hand)

        <match key="smbios.system.product" string="MacBook1,1">
          <spawn udi="/org/freedesktop/Hal/devices/macbook_backlight"/>
        </match>
        <match key="smbios.system.product" string="MacBook1,2">
          <spawn udi="/org/freedesktop/Hal/devices/macbook_backlight"/>
        </match>
        <match key="smbios.system.product" string="MacBook2,1">
          <spawn udi="/org/freedesktop/Hal/devices/macbook_backlight"/>
        </match>
        <match key="smbios.system.product" string="MacBook2,2">
          <spawn udi="/org/freedesktop/Hal/devices/macbook_backlight"/>
        </match/>

---

### Post by pveith on 2007-06-14
In newer macbooks the bios-data has changed. The line

```
 <match key="smbios.system.manufacturer" string="Apple Computer, Inc.">
```

has to be changed to 

```
 <match key="smbios.system.manufacturer" string="Apple Inc.">
``` in file /usr/share/hal/fdi/policy/10osvendor/10-macbook-backlight.fdi (and probably in /usr/share/hal/fdi/policy/10osvendor/10-macbookpro-utils.fdi, too). This will break older macbook support, so this is just a dirty fix.

You can look up if your bios is affected by using System -> Preferences -> Hardware Information and look under "Computer / extended" key "smbios.system.manufacturer". My new 2,16 GHz macbook reads "Apple Inc." not like older version which had "Apple Comupter, Inc.".

This took me quite a while to figure out. So hopefully this helps someone, too...

---

### Post by kzm. on 2007-06-20
i can confirm the "Apple Comupter, Inc" to "Apple Inc." solution. nice!

thanx a lot

---

### Post by FearlessSpiff on 2007-11-23
What about the newest MacBook SantaRosa 2.2GHz? I cannot make the backlight work with Gutsy! :-(

---

