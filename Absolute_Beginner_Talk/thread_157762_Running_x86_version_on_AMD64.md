---
title: "Running x86 version on AMD64"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by Azio on 2006-04-09
Is it possible to load the x86 version of Ubuntu on my AMD64 box? I've successfully managed to get the AMD64 version working on here but the x86 version just won't start... I'm not sure if this is because it doesn't like my CPU or something else is wrong with it. If it's just my CPU then it resolves a lot of confusion on my end.

---

### Post by rado_london on 2006-04-09
May I ask why you want to do such thing. 
However the 64 bit ubuntu has compiled programs for that particular architechture and probably wont work

---

### Post by Azio on 2006-04-09
[QUOTE=rado_london]May I ask why you want to do such thing. [/QUOTE]
I'm told that the x86 version will give me better performance in 32-bit apps than the 64-bit version. That and I'm a noob and I'm not exactly thrilled by the idea of having to deal with the inevitable compatibility problems if I run the 64-bit version.

---

### Post by dcstar on 2006-04-09
[QUOTE=Azio]I'm told that the x86 version will give me better performance in 32-bit apps than the 64-bit version. That and I'm a noob and I'm not exactly thrilled by the idea of having to deal with the inevitable compatibility problems if I run the 64-bit version.[/QUOTE]
Don't use the x86 kernels, select the K7 kernel after install (AMD optimised).

As well, there are AMD optimised builds of Firefox available ("Swiftfox").

---

### Post by steve.horsley on 2006-04-10
[QUOTE=Azio]Is it possible to load the x86 version of Ubuntu on my AMD64 box? I've successfully managed to get the AMD64 version working on here but the x86 version just won't start... I'm not sure if this is because it doesn't like my CPU or something else is wrong with it. If it's just my CPU then it resolves a lot of confusion on my end.[/QUOTE]
Yes it is. In fact, I am running 32-bit Ubuntu on my AMD64 at the moment. My main reason for going with a 32-bit kernel is that I gather multimedia codecs are a problem on 64-bit. I actually wnet ahead and installed the k7 kernel once the base install was running.

So if you are having problems with the standard x86 install, I don't know why, but it's not a basic processor incompatibility.

---

