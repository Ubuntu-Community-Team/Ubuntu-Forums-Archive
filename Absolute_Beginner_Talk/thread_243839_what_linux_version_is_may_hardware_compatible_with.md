---
title: "what linux version is may hardware compatible with?"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by mykalreborn on 2006-08-25
first of all, i would like to apollogize if i'm in the wrong section of the forum:)
i've been searching long and hard on the internet for tiny linuxes with pretty much no gui and i allways bump into the same problem: my hardware configuration.
i have a vague idea of what kind of linux i should get, but i would very much like to hear the opinion of someone who knows this stuff.
so i have an AMD Sempron 2800+ processor (acpi/authenticamd_-_X86_family_15_model_44/_0).
i figured out on my own that i should use a i86 version of linux(hope that's right), but i'm not sure if this is the only name this configuration was given.
so what i'm asking you, is if you could give me some links to the types of linuxes suttable for my configuration.
thanks a lot!

---

### Post by derred on 2006-08-25
The best thing to do for a quick fix (in ubuntu at least) is to get one of the premade kernels(eather 686 or k7) and install it with apt. If you want to know how exactly to do that(it's very easy) go to his thread [http://ubuntuforums.org/showthread.php?t=85917]("http://ubuntuforums.org/showthread.php?t=85917")
The alternative is to compile your own kernel and that's a bit much me :D  as I've only been 100% linux for 3 weeks, but if you really want to do it then I sugest you read(or follow the steps of) this howto: [http://www.ubuntuforums.org/showthread.php?t=217657&highlight=kernel.org+kernel+compile]("http://www.ubuntuforums.org/showthread.php?t=217657&highlight=kernel.org+kernel+compile")

Hope the information will prove helpfull to you and please post your progress or any more questions. 
Have a nice day! :cool:

---

### Post by az on 2006-08-25
Just install ubuntu and the default 386 kernel will work fine.  You can then install the k7 kernel (not the 686 one - that's only for a Pentium) for an every-so-slight performance gain.

sudo apt-get install linux-k7

---

### Post by wpshooter on 2006-08-25
Just download, burn, & install the **DESKTOP** 32 bit version of Ubuntu 6.06.1 LTS and you will be good to go.  With that speed processor you should have great preformance.

---

### Post by Jerome36 on 2006-08-25
Ya', you should be fine, with that processor.  I began reading your post thinking you had something REALLY old, and needed something like DSL (Damn Small Linux), but what you have isn't bad at all.

---

### Post by mykalreborn on 2006-08-25
thanks for the help. it's okay now. i've relised i'm much to new in linux to drop the gui (and why should i not use it in the first place :P). so i installed ubuntu again on my system and it works fine.

---

