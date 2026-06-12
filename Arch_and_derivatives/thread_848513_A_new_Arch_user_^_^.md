---
title: "A new Arch user ^_^"
date: 2008-07-03
forum: Arch and derivatives
---

### Post by atomkarinca on 2008-07-03
I have finally set up everything as I wanted now w00t :)

And the tasks weren't easy: Jack server with Ardour, Hydrogen and Rosegarden; Timidity++ with Rosegarden and TuxGuitar; SCIM with Anthy support; Nvidia drivers. I should say it wasn't as hard as I expected. In fact it was rather easy. OK I admit I cheated a little bit, used the beginnersguide.txt from cd and then looked at it fron the website with lynx installed.

I don't know exactly why but I love my Arch now. Openbox is set up the way I'm used to and it's faster than Ubuntu.

Only problem left is I couldn't get wicd working. I tried a couple of threads but no luck. Even something for changing my DNS server is enough.

Gotta love Arch :)

---

### Post by Dr Small on 2008-07-03
Welcome aboard, matey :)

---

### Post by RiceMonster on 2008-07-04
Welcome. Arch is great.

---

### Post by Barrucadu on 2008-07-04
Welcome. You do realise you can never leave, right?

---

### Post by ruffEdgz on 2008-07-04
Wonderful to see another arch user!!

Welcome aboard :D

---

### Post by atomkarinca on 2008-07-04
> **Barrucadu said:**
> Welcome. You do realise you can never leave, right?

At first I didn't believe that but I think it's true.

---

### Post by DrOlaf on 2008-07-04
> **atomkarinca said:**
> 
Only problem left is I couldn't get wicd working. I tried a couple of threads but no luck. Even something for changing my DNS server is enough.

Gotta love Arch :)

Welcome to the club. I can sympathise with you about wicd - I couldn't get it to work on my Acrh either. The built-in scripts work fine though, as long as I configure my router to use WEP. I'm still struggling to get WPA working.

---

### Post by atomkarinca on 2008-07-04
> **DrOlaf said:**
> Welcome to the club. I can sympathise with you about wicd - I couldn't get it to work on my Acrh either. The built0in scripts work fine though, as long as I configure my router to use WEP. I'm still struggling to get WPA working.

Don't get me wrong I have no problem with networking but if I could get Wicd working then I could change my DNS server, that's all.

---

### Post by RiceMonster on 2008-07-04
Wicd works perfectly for me. I just followed the guide in the arch wiki. I'm using an intel wireless card.

---

### Post by DrOlaf on 2008-07-05
> **RiceMonster said:**
> Wicd works perfectly for me. I just followed the guide in the arch wiki. I'm using an intel wireless card.

That's probably my problem - my Arch notebook has a Ralink card. The  rt2x00 drivers in the repos work OK with WEP, but I thought I'd try to compile the CVS ones to see if I could get WPA to work. I'm posting this from my Ubuntu machine while I finish off the Arch reinstallation that I had to do as a result :)

---

### Post by ShodanjoDM on 2008-07-05
> **atomkarinca said:**
> Gotta love Arch :)

+1

I'm enjoying Arch more and more everyday. Currently I'm in the process of replacing most of my installed pre-packaged apps by rebuilding them through ABS.

Now firefox runs even faster & lighter :D

---

### Post by mips on 2008-07-05
> **DrOlaf said:**
> That's probably my problem - my Arch notebook has a Ralink card. The  rt2x00 drivers in the repos work OK with WEP, but I thought I'd try to compile the CVS ones to see if I could get WPA to work. I'm posting this from my Ubuntu machine while I finish off the Arch reinstallation that I had to do as a result :)

Let us know how it goes. I have a rt2500 in my desktop that I have never used. Wondering if the rt2x00 drivers support AP mode yet? Would love to turn my desktop into a AP so I can run my laptop off it.

---

### Post by MisfitI38 on 2008-07-05
> **ShodanjoDM said:**
> +1

I'm enjoying Arch more and more everyday. Currently I'm in the process of replacing most of my installed pre-packaged apps by rebuilding them through ABS.

Now firefox runs even faster & lighter :D

Have you checked out [pacbuiler?]("http://bbs.archlinux.org/viewtopic.php?id=48957")

---

### Post by Inxsible on 2008-07-11
> **ShodanjoDM said:**
> +1

I'm enjoying Arch more and more everyday. Currently I'm in the process of replacing most of my installed pre-packaged apps by rebuilding them through ABS.

Now firefox runs even faster & lighter :D

> **MisfitI38 said:**
> Have you checked out [pacbuiler?]("http://bbs.archlinux.org/viewtopic.php?id=48957")I was wondering if there was really a noticeable difference in speed once the apps were re-built?

Isn't Arch optimized for i686 and x86_64 ? Isn't that one of the selling points for Arch?

And if they are optimized...what would rebuilding the packages give you that a standard install doesn't?

---

### Post by MisfitI38 on 2008-07-11
> **Inxsible said:**
> I was wondering if there was really a noticeable difference in speed once the apps were re-built?

No. It will come down to placebo.
> 
Isn't Arch optimized for i686 and x86_64 ? Isn't that one of the selling points for Arch?
Yes. Compiling for i686 vs compiling for i386 will give a very slight, *potential* performance advantage. Further optimizing for specific architectures will give virtually no advantage. Anyone who disagrees with this is most likely a 1337 ricer.
> 
And if they are optimized...what would rebuilding the packages give you that a standard install doesn't?
I suggested pacbuilder because there is no harm in ricing, and this is all just for fun, anyway. ;)
Rebuilding your whole system is a very time consuming process, needless to say. Is it practical? Never. Do some people enjoy it?
Curiously, some people love this ****. :D

---

### Post by Inxsible on 2008-07-11
> **MisfitI38 said:**
> Anyone who disagrees with this is most likely a 1337 ricer.LMAO !!!

That's funny !!

Love that term ricer :)

---

### Post by Barrucadu on 2008-07-11
The benefit of compiling everything yourself is that you can optimize for your specific processor (which will give you a nice placebo effect), or specify custom options during compile (such as stripping features you don't need, which has a much better chance of making it faster).

---

### Post by Inxsible on 2008-07-11
> **Barrucadu said:**
> The benefit of compiling everything yourself is that you can optimize for your specific processor (which will give you a nice placebo effect), or specify custom options during compile (such as stripping features you don't need, which has a much better chance of making it faster).
But considering the fact that Arch is pretty minimalist anyway....and the user has to manually add everything he wants...what are the remaining features that one can strip further - making sure that the OS works properly, of course !!

---

### Post by MisfitI38 on 2008-07-11
> **Barrucadu said:**
> The benefit of compiling everything yourself is that you can optimize for your specific processor (which will give you a nice placebo effect), or specify custom options during compile (such as stripping features you don't need, which has a much better chance of making it faster).

Well, I certainly respectfully disagree. Disabling options does not make anything faster. 
Say you install a package which has arts support. You recompile it, removing support for arts. Will it perform faster? No.
Wars have been started over this topic for years, but as time moves forward and CPU's get ever faster and GCC improves, there is less and less reason to rebuild your whole system.

The most clogged bottleneck in a machine is still the harddrive, not the CPU, by any stretch. ;)

---

### Post by Barrucadu on 2008-07-12
> **MisfitI38 said:**
> The most clogged bottleneck in a machine is still the harddrive, not the CPU, by any stretch. ;)

Which is why playing with ramfs and tmpfs is fun :D

---

### Post by MisfitI38 on 2008-07-12
> **Barrucadu said:**
> Which is why playing with ramfs and tmpfs is fun :D
Exactly. :D
Ricing is harmless..and besides, we are all using Arch because we love to tinker anyways, right? :)

---

### Post by DrOlaf on 2008-07-22
> **mips said:**
> Let us know how it goes. I have a rt2500 in my desktop that I have never used. Wondering if the rt2x00 drivers support AP mode yet? Would love to turn my desktop into a AP so I can run my laptop off it.

Well, mips, I'm afraid I gave up on my ralink card. Try as I might, I couldn't get the rt2x00 drivers to work with my Linksys WRT54G using WPA. In the end I ponied up 20 bucks for an Atheros card and that works fine. 

The ralink card worked fine with WEP, but I never tried to set it up as an AP.

---

