---
title: "Ubuntu/Windows/Mac - Puzzling question"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Elicaris on 2007-05-28
This has been puzzling me ever since I first read about Linux a few years back. Why isnt linux a universal OS? Why can't it run Windows/Mac software? If it is possible why isnt it already available? I'm sorry if this is a stupid question but I don't know how difficult coding is or exactly how an OS is put together. I'm just so sick of the crap Microsoft is dishing out...


-Elic-

---

### Post by Gmbrdilos on 2007-05-28
remember those things you played with in kindergarten? the thing with 3 holes (square circle and triangular) using mac/windows software on linux is like trying to squeeze the cube into the round hole. The beauty of open source software is that when a program is made for a specific platform, others can study the source code and attempt to make a version for another platform.

---

### Post by bobplano on 2007-05-28
no OS is universal because they each have their own API's. programs are programed to run on certain APIs. windows is more popular so it seems like it is more "universal" but that's only because many people are using it.

---

### Post by mattva01 on 2007-05-28
Well because most programs use "hooks" in the OS in order to accomplish things faster or in a less complicated fashion. The issue is these hooks are different in different operating systems. Not sure if that is the greatest explanation but I hope it helps.

---

### Post by Elicaris on 2007-05-28
Is it difficult to make a multi API OS or am'I getting ahead of myself? :P

> **bobplano said:**
> no OS is universal because they each have their own API's. programs are programed to run on certain APIs. windows is more popular so it seems like it is more "universal" but that's only because many people are using it.

---

### Post by mattva01 on 2007-05-28
Its not thats its that  difficult, its just that its more profitable for the companies to make the API only usable on their systems.

---

### Post by bobplano on 2007-05-28
well windows and mac aren't going to release their APIs because thats basically how the operating system runs. the project wine is trying to recreate windows' apis as best they can though.

---

### Post by p_quarles on 2007-05-28
> **mattva01 said:**
> Its not thats its that  difficult, its just that its more profitable for the companies to make the API only usable on their systems.

Exactly. Why make it easy for people when you can lock-in customers?

---

### Post by Elicaris on 2007-05-28
> **mattva01 said:**
> Its not thats its that  difficult, its just that its more profitable for the companies to make the API only usable on their systems.

True, but since Ubuntu is a free OS wouldnt it be benificial for them to make a multi-API update to catch the attention of current Windows users? I'm sure Vista users would start using their discs as skeet if that idea ever became a reality. :)

---

### Post by bobplano on 2007-05-28
you'd need the exact API's of windows vista or OS X so the programs can run. the APIs are closed source so for programs like wine, they are just guessing at API's. so unless it's windows or apple APIs then there is no point in adding more because it doesn't need any more

---

### Post by mattva01 on 2007-05-28
The issue is not whether its possible, its whether its legal. Most of these API's have multiple patents and other legal defenses associated with them.

---

### Post by Elicaris on 2007-05-28
> **mattva01 said:**
> The issue is not whether its possible, its whether its legal. Most of these API's have multiple patents and other legal defenses associated with them.


   Very true, but since WINE/Cedega run a fair amount of windows software what's really holding Ubuntu from trying to integrate that into their OS?  If WINE/Cedega were breaking any legal patents they would've been in a lot of legal problems years ago.

---

### Post by mattva01 on 2007-05-28
> **Elicaris said:**
> Very true, but since WINE/Cedega run a fair amount of windows software what's really holding Ubuntu from trying to integrate that into their OS?  If WINE/Cedega were breaking any legal patents they would've been in a lot of legal problems years ago.
Actually the Novell documents reveal that Microsoft believes WINE to be in violation of their patents.

---

### Post by Gmbrdilos on 2007-05-28
> **Elicaris said:**
> Very true, but since WINE/Cedega run a fair amount of windows software what's really holding Ubuntu from trying to integrate that into their OS?  If WINE/Cedega were breaking any legal patents they would've been in a lot of legal problems years ago.

wine is experminetal and not guaranteed to work.
and as mattva01 mentions, microsoft thinks its illegal

---

### Post by SoulinEther on 2007-05-28
That'll be the day, when you see a *nix OS shipped on a PC with WINE by default. Or any API emulating software for that matter...... Microsoft v. Open Source, well.. not open source, but ... the parties involved in the matter.

---

### Post by Elicaris on 2007-05-28
> **Gmbrdilos said:**
> wine is experminetal and not guaranteed to work.
and as mattva01 mentions, microsoft thinks its illegal

  If it were to be illegal it would have to be an exact copy of Microsofts API right? Since WINE isnt an exact copy it can't be illegal or else wouldnt for example Tylenol and Advil be in a legal fight for making two medications for relieving headaches(maybe a bad example but I hope you got the idea)?

---

### Post by mattva01 on 2007-05-28
Well there is a project called LINA that is promising to convert Linux apps to run with the native API's of several different OSs.

---

### Post by mattva01 on 2007-05-28
> **Elicaris said:**
> If it were to be illegal it would have to be an exact copy of Microsofts API right? Since WINE isnt an exact copy it can't be illegal or else wouldnt for example Tylenol and Advil be in a legal fight for making two medications for relieving headaches(maybe a bad example but I hope you got the idea)?

No thats the issue with patents, they are for the idea, not the implementation.

Also, drugs like Advil automatically lose patents after a certain period of time.(Sort of, the situation is rather complicated)

---

### Post by SoulinEther on 2007-05-28
Well, I don't think it has to be a "copy" for it to be illegal.... if somebody patents or copyrights a concept, and if (later) you happen to stumble upon the same design without looking at the patent or copyright already in existance... it's in violation of the original patent/copyright if you try to take it and use it like on a wide scale operation.

If I write three characters ffc and copyright that for my company, and someone else randomly comes up with those three letters... I think that's what i'm trying to say.

---

### Post by macogw on 2007-05-28
> **Elicaris said:**
> If it were to be illegal it would have to be an exact copy of Microsofts API right? Since WINE isnt an exact copy it can't be illegal or else wouldnt for example Tylenol and Advil be in a legal fight for making two medications for relieving headaches(maybe a bad example but I hope you got the idea)?

exact copy of code = copyright violation
same general idea = patent violation

both are illegal

---

### Post by SoulinEther on 2007-05-28
> **macogw said:**
> exact copy of code = copyright violation
same general idea = patent violation

both are illegal

There ya go, that's what I was getting at.

---

### Post by Elicaris on 2007-05-28
> **macogw said:**
> exact copy of code = copyright violation
same general idea = patent violation

both are illegal

   Ah, I see... that was a rough blow. I guess my question for a Multi-API has been answered and an idea destroyed lol.  I guess it's upto companies to make software compatible to each OS...

---

### Post by macogw on 2007-05-28
> **Elicaris said:**
> I guess it's upto companies to make software compatible to each OS...

Now if only we could convince them that Linux is used outside the server room and that we would like to use their software too (provided a better free alternative doesn't exist, because that's just bad economics).

---

### Post by SoulinEther on 2007-05-28
Or for the OS companies to merge. Or for some of the OS's to die and let only one survive.

If there's only one OS in existence, there's absolutely no need to cater to all of them and design software for all of them.

But who doesn't like choice? :S

---

### Post by Gmbrdilos on 2007-05-28
> **macogw said:**
> Now if only we could convince them that Linux is used outside the server room and that we would like to use their software too (provided a better free alternative doesn't exist, because that's just bad economics).

people tend to think that idiot friendly (example: windows or mac) means better

---

### Post by Gmbrdilos on 2007-05-28
> **SoulinEther said:**
> Or for the OS companies to merge. Or for some of the OS's to die and let only one survive.

If there's only one OS in existence, there's absolutely no need to cater to all of them and design software for all of them.

But who doesn't like choice? :S

"Choice. The problem is Choice." - Neo, Matrix Reloaded

---

### Post by mattva01 on 2007-05-28
Diverse API's aren't bad. It's just when you are not allowed to use them without a license that things get nasty.

---

### Post by Elicaris on 2007-05-28
> **SoulinEther said:**
> Or for the OS companies to merge. Or for some of the OS's to die and let only one survive.

If there's only one OS in existence, there's absolutely no need to cater to all of them and design software for all of them.

But who doesn't like choice? :S

   In a way thats what it's like now, the one OS on the top of the food chain has been half assed for years. What we DO need like you said is a choice.

---

### Post by mattva01 on 2007-05-29
> **Gmbrdilos said:**
> people tend to think that idiot friendly (example: windows or mac) means better
Calling Windows idiot friendly is like calling Steve Ballmer friendly (ok that was a horrible joke)

---

### Post by SoulinEther on 2007-05-29
> **Elicaris said:**
> In a way thats what it's like now, the one OS on the top of the food chain has been half assed for years. What we DO need like you said is a choice.
The problem lies in lack of choice. I like Linux, but if there's no competition to make it improve over time (ie windows and mac), it'll become just like what Windows is today.

It's just like how hell makes heaven all that much better. If you don't have Wndows, you'll never enjoy Linux.

---

### Post by mattva01 on 2007-05-29
Competition is a great catalyst for innovation. Thats why warfare sometimes has some very beneficial after-effects from military research. Without  any enemies, why bother?

---

### Post by Elicaris on 2007-05-29
> **SoulinEther said:**
> The problem lies in lack of choice. I like Linux, but if there's no competition to make it improve over time (ie windows and mac), it'll become just like what Windows is today.

It's just like how hell makes heaven all that much better. If you don't have Wndows, you'll never enjoy Linux.

    In a way, but from what I can see Linux has some great potential if companies listen closer to what the people need. Or else how long will it take to evolve?

---

### Post by Gmbrdilos on 2007-05-29
> **Elicaris said:**
> In a way, but from what I can see Linux has some great potential if companies listen closer to what the people need. Or else how long will it take to evolve?

I'd rather see a competition between different distros of linux than a competition linux vs windows

---

### Post by Elicaris on 2007-05-29
> **Gmbrdilos said:**
> I'd rather see a competition between different distros of linux than a competition linux vs windows

       but wouldnt you want one OS that can do it all? :P

---

### Post by Gmbrdilos on 2007-05-29
> **Elicaris said:**
> but wouldnt you want one OS that can do it all? :P

most if not all linux is software is compatible between different distributions
the purpose of the competition would probably be the packages that come with default installation

---

### Post by SoulinEther on 2007-05-29
> **Gmbrdilos said:**
> most if not all linux is software is compatible between different distributions
the purpose of the competition would probably be the packages that come with default installation

Now that's tedious.

---

