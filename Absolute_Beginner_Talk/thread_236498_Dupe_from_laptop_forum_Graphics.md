---
title: "Dupe from laptop forum Graphics"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by Jjohn on 2006-08-14
Sorry mods this is already posted but I am not getting a response so thought to try here 
Acer Aspire 5000 Graphics 

--------------------------------------------------------------------------------

Hi all 
I am trying to get some graphics accelleration from my:
SiS 661/741/760/760/761 PCI/AGP VGA Display Adapter.
Is there any hope for me ????

---

### Post by em3raldxiii on 2006-08-14
I am not 100% sure what we're looking for here.  Is it that your display adapter is on-board?  Or are you asking for a separate video card?
 
If it's onboard, then we have to look for your motherboard support I think.  If it's a separate card, then if we knew the make/model it would likely be easier to help.

---

### Post by Jjohn on 2006-08-15
Hi Emerald,
          Thank you for your response. Here is a history of what happened. 
          I own an Acer aspire 5000 laptop AMD64 1.6 mhz processor all graphics are on the motherboard 
         I installed the amd 64 Ubuntu distro. This was a mistake as there are many things in 64bit that are not working. Most of the screen savers and anything with more than basic movenment would not work. The output from [code]glxinfo returned a "no gl info." I then installed the regular 32bit distro and things improved significantly all screensavers now work and programmmes requiring accelleration DO work but are crippled (totally slow refresh rate) [code] glxinfo now gives lots of output including the line no direct rendering 
       My linux is not on line so I need to retype any outputs you may need but I can do that.
What kind of info do you need me to write??:-k

---

### Post by em3raldxiii on 2006-08-15
I might be able to get what I need ... give me a couple of minutes and I'll do some quick searching :D  I'm sure we (or someone) can get you up and running here :D

---

### Post by em3raldxiii on 2006-08-15
Kay, after some figuring and searching the forums, I found this old link.  It looks like the original poster had a different laptop, but it also seems that his/her solution worked for at least at least one other (different) laptop.  You have the same graphics chipset as this person as well.
 
I'll let you know if I find anything else.  If this solution DOES work for you, please comment here AND on the other thread so that others in your position can get their fixed as well :D
 
[http://www.ubuntuforums.org/showthread.php?t=136183](http://www.ubuntuforums.org/showthread.php?t=136183)

---

### Post by em3raldxiii on 2006-08-15
One more thing, according to ACER's website, your graphics chipset is also known as "Mirage 2" this may help if you do any other searching.

---

### Post by Jjohn on 2006-08-15
Thanks for the quick response,
     I will give that "mirage2" a good google and let both threads know what the outcome is...:-D

---

### Post by Jjohn on 2006-08-17
Hi All,
       Having read the links you submitted I am as unsure now as I was before.
       The authority on this has stated that 3d accelleration is not and will not be available for this chipset in a linux environment. However 2d up to direct x 8.1 should be achievable.
       Is changing my screen resolution going to give me improved 2d accelleration somehow or is the resolution a side issue not related to my requirements??:sad:

---

