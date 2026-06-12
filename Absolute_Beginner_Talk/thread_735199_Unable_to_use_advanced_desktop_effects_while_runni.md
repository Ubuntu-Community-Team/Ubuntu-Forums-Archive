---
title: "Unable to use advanced desktop effects while running gutsy from my ps3"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by dferg24 on 2008-03-25
I realize that this topic has been touched on in other threads but none of them have helped me so far.

I just recently installed gutsy 7.1 on my PS3 and have applied the appropriate updates using the update manager as far as I know.

Every thread I have read basically says to install compiz. Which I have done using the add/remove applications software. I can get access to the advanced desktop effects and activate them but under appearances I am unable to run the extra visual effects because it just keeps saying desktop effects can not be enabled.

Please help point me in the right direction if there is a solution out there.

Thanks in advance

---

### Post by confused57 on 2008-03-25
> **dferg24 said:**
> I realize that this topic has been touched on in other threads but none of them have helped me so far.

I just recently installed gutsy 7.1 on my PS3 and have applied the appropriate updates using the update manager as far as I know.

Every thread I have read basically says to install compiz. Which I have done using the add/remove applications software. I can get access to the advanced desktop effects and activate them but under appearances I am unable to run the extra visual effects because it just keeps saying desktop effects can not be enabled.

Please help point me in the right direction if there is a solution out there.

Thanks in advance
You would need a video card/chipset with appropriate drivers to enable desktop effects.  Have you tried System---Administration---Restricted Drivers Manager to see if there is a driver available for your video card?

---

### Post by Confuzius on 2008-03-25
I was under the impression that the playstation did not grant 3rd party(non-sony approved) access to the 3d hardware, almost to prevent people from buying ps3's just to hack into a very decent cheap computer.
It may not actually be possible, but I could be wrong.

---

### Post by donnyblaze1 on 2008-03-25
Try plugging this into your favorite terminal:
```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

After this you should be able to configure compiz as per usual.

Good luck!

---

### Post by joshrobinson on 2008-03-25
> **Confuzius said:**
> I was under the impression that the playstation did not grant 3rd party(non-sony approved) access to the 3d hardware, almost to prevent people from buying ps3's just to hack into a very decent cheap computer.
It may not actually be possible, but I could be wrong.

last i tried, this was the case, so your correct
you have no 3d acceleration, hence no compiz

---

### Post by dferg24 on 2008-03-26
Thanks for everyones help.

 I tried your suggestions with unfortuneately no success and upon a little more research found out that Sony's graphics card is in fact not fully supported by linux at the moment and there is no way enable 3d graphics. 

hopefully full support will come soon

---

### Post by kolisikepu on 2008-03-26
Isn't PS3 running nVidia?  If not, do you know the model of the chip or any info on the chip?

---

### Post by Trail on 2008-03-26
As far as I have heard, it is intentional from Sony's part.

---

### Post by kolisikepu on 2008-03-26
... why don't you just comment out all video cards in the Compiz blacklist??

```
sudo gedit /usr/bin/compiz
```

And then comment out all these lines...
```
# blacklist based on the pci ids
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
T=" 1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12" # intel 965
T="$T 8086:2972" # i965 (x3000)
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700

```

add this line just before BLACKLIST_PCIIDS="$T"
```
T=""
```

Try it with that extra line and if it still doesn't work, then comment it out.

I'm really hoping that this would work because if it does, then I'll be saying Hello to Ubuntu Community from my PS3 too... ;) \\:D/

---

### Post by kolisikepu on 2008-03-26
dferg24,

I'm hoping you'll come back with a quick reply... quite keen to find out how you went.

:popcorn::popcorn::popcorn::popcorn::popcorn::popcorn::popcorn::popcorn:

---

### Post by dferg24 on 2008-03-26
I have tried all the suggestions within this thread and also many other threads and really dont think its possible until the graphics card in the ps3 is fully supported.

So no advanced effects yet!

Thanks to everyone for helping.

---

### Post by kolisikepu on 2008-03-26
Even blacklisting??  

aaaaarrrrrgggghhh.....

---

### Post by dferg24 on 2008-03-26
ya the blacklisting thing never worked for me.
I am brand new to linux though so that doesnt necessarily mean it wouldnt work for someone who knew what they were doing.

But unfortuneately everything I try I cant get them enabled and pretty much everything else Ive tried Ive been able to do so I think I might give up on it for now.

---

