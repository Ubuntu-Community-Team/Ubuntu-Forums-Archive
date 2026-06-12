---
title: "Automatix and upgrade"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Oki on 2007-01-31
Today’s question;

I have read several times that Automatix2 can make problems for the user if he/her tries to upgrade the system, since the system don’t know about what Autmatix has done. 

Question;
Automatix2 gives you the choice to uninstall the programs that has been installed with it. If you uninstall all from Automatix before upgrading, will the danger for a system brake still be there? 

Could easyubuntu make the same problems when upgrading?

As always; Thanks for your answer

---

### Post by jackrobinson on 2007-01-31
> **Oki said:**
> Today’s question;

I have read several times that Automatix2 can make problems for the user if he/her tries to upgrade the system, since the system don’t know about what Autmatix has done. 

Question;
Automatix2 gives you the choice to uninstall the programs that has been installed with it. If you uninstall all from Automatix before upgrading, will the danger for a system brake still be there? 

Could easyubuntu make the same problems when upgrading?

As always; Thanks for your answer
The real issues come from broken packages in Ubuntu main (not automatix or easy ubuntu). The breakages reported by users who tried to upgrade from dapper to edgy was because of these broken packages released by Ubuntu.

---

### Post by sketchone on 2007-01-31
im bit of a noob so this more my expierience than advice, iv used automatix2 a few times now while playing with ubuntu and have never had a problem, i have been able to install and uninstall software perfectly without anything breaking.

---

### Post by jackrobinson on 2007-01-31
> **sketchone said:**
> im bit of a noob so this more my expierience than advice, iv used automatix2 a few times now while playing with ubuntu and have never had a problem, i have been able to install and uninstall software perfectly without anything breaking.

yes fact is Ubuntu did a shoddy job with Edgy and hence users who tried to upgrade from Dapper to Edgy experienced breakages and some folks who did not understand what was going on blamed it on Automatix.

---

### Post by lyceum on 2007-01-31
I have upgreaded a few PC's with Automatix on them (2) with no problems, so I really don't know what the problem is, as I have not run into it. Has anyone had these problems that could explain what happened and if they were fixable?

---

### Post by jackrobinson on 2007-01-31
> **lyceum said:**
> I have upgreaded a few PC's with Automatix on them (2) with no problems, so I really don't know what the problem is, as I have not run into it. Has anyone had these problems that could explain what happened and if they were fixable?

I upgraded from Dapper to Edgy on a machine which did not have automatix on it and the upgrade failed with several broken packages like udev etc. I knew how to fix the issues and hence succeeded finally in getting Edgy up and running.. and no I wasn't using any third party repositories either.

---

### Post by Oki on 2007-01-31
jackrobinson:
Are you sure? I just read in a blogg yesterday from one of the guys in the Ubuntu team asking ”Do you need Automatix”. All the comments where talking about that Automatix could break the system when upgrading. 

sketchone:
I am not talking about breaking your system on the daily basic, when updating the system or when installing different application. But I am talking about breaking the system when upgrading; meaning upgrading from example Ubuntu Dapper Drake to Ubuntu Edgy.

---

### Post by lyceum on 2007-01-31
> **jackrobinson said:**
> I upgraded from Dapper to Edgy on a machine which did not have automatix on it and the upgrade failed with several broken packages like udev etc. I knew how to fix the issues and hence succeeded finally in getting Edgy up and running.. and no I wasn't using any third party repositories either.

That is what I was thinking, that it is the programs Automatix installs, not Automatix that causes the problems. SO if there was a list of those programs, couldn't they just be un-installed and then re-installed after the upgrade?

---

### Post by jackrobinson on 2007-01-31
> **Oki said:**
> jackrobinson:
Are you sure? I just read in a blogg yesterday from one of the guys in the Ubuntu team asking ”Do you need Automatix”. All the comments where talking about that Automatix could break the system when upgrading. 
Well this is how it works: Ubuntu knows its done a shoddy job with Edgy. Now who to blame? ok, lets blame automatix since a lot of people dont like its creator. So a couple of lower rung devs blog about how automatix can potentially break an upgrade (with no real evidence) and then folks who do not like the concept of automatix (automating things) and also people who dont like its creator gang up and start filling blogs with one standard line: "Automatix breaks upgrades". If anybody ever asked them to elaborate, they would not be able to substantiate except saying stuff like "its a well known fact or a dev blogged about it"

---

### Post by jackrobinson on 2007-01-31
> **lyceum said:**
> That is what I was thinking, that it is the programs Automatix installs, not Automatix that causes the problems. SO if there was a list of those programs, couldn't they just be un-installed and then re-installed after the upgrade?
Automatix mostly installs packages from the official Ubuntu repositories. If those packages themselves are broken, nothing much that Automatix can do about it.
Also, as I said, the upgrade on my machine broke and I did not even install or use Automatix.

---

### Post by lyceum on 2007-01-31
> **jackrobinson said:**
> Well this is how it works: Ubuntu knows its done a shoddy job with Edgy. Now who to blame? ok, lets blame automatix since a lot of people dont like its creator. So a couple of lower rung devs blog about how automatix can potentially break an upgrade (with no real evidence) and then folks who do not like the concept of automatix (automating things) and also people who dont like its creator gang up and start filling blogs with one standard line: "Automatix breaks upgrades". If anybody ever asked them to elaborate, they would not be able to substantiate except saying stuff like "its a well known fact or a dev blogged about it"

Really? I see stuff posted all over the place about Edgy being "edgy" and unstable. Not to be rude, I have not heard any of this before. I thought it might be a rummor, but is this really how it got started and why would people not like the guy that came up with Automatix? It was a great idea and it works?!?!

---

### Post by Oki on 2007-01-31
So the problem is not with the Automatix. Ok, thank you for clearing this up for me. Lets hope they do a better job with Feisty Fawn, witch will be my next stop:-) 

As a sidenote; coming from Windows I am so used to the “clean install” so I am happy even though the upgrade is not so good with Ubuntu.

---

### Post by jackrobinson on 2007-01-31
> **lyceum said:**
> Really? I see stuff posted all over the place about Edgy being "edgy" and unstable. Not to be rude, I have not heard any of this before. I thought it might be a rummor, but is this really how it got started and why would people not like the guy that came up with Automatix? It was a great idea and it works?!?!

Personal issues I would think. In any case the fact that Automatix is independent and is also used by so many people does not go down well with the Ubuntu team. Ubuntu should seriously think of collaborating with Automatix.

---

### Post by lyceum on 2007-01-31
> **jackrobinson said:**
> Ubuntu should seriously think of collaborating with Automatix.

I agree. It is an easy way for new uses to get up to specks quickly, though I see things in the FF notes that will make Automatix less useful, as they will are ready work in FF. But there will always be things like Flash and Adobie that cannot come by defult. Heres for hoping!

---

### Post by Pugwash on 2007-01-31
I installed opera with automatix initially, when I tried to install the flash plugin, it just wasn't detecting opera. I decided to uninstall it (via automatix) and install opera manually using the terminal, solved the problem. I can enjoy some youtube,

---

### Post by Oki on 2007-01-31
“*In any case the fact that Automatix is independent and is also used by so many people does not go down well with the Ubuntu team.*”

This sounds strange, I believed that Ubuntus goal was to fix bug 1, and Automatix is(perhaps not so much now since most of the package can bee found in Synaptic/Adpet), a good tool for newbie’s like I was(and I guess, still are). Automatix let people see how Ubuntu/kubuntu and its applications works before learning how the system works. This can give them the further interests - I think. And if they don’t see that “need”, they have a problem. 

Perhaps I am a bit naive (just read about Launchpad witch I didn’t like, witch surprised me in a negative way). 

But if you read that blog you will understand that the blogger don’t care much about it, like; “I don’t use it”, “have never used it”, “seen it once”, “I like to know how my system works” and so on… 

But; thanks for all your answers!

---

### Post by lyceum on 2007-01-31
> **Oki said:**
> “*In any case the fact that Automatix is independent and is also used by so many people does not go down well with the Ubuntu team.*”

This sounds strange, I believed that Ubuntus goal was to fix bug 1, and Automatix is(perhaps not so much now since most of the package can bee found in Synaptic/Adpet), a good tool for newbie’s like I was(and I guess, still are). Automatix let people see how Ubuntu/kubuntu and its applications works before learning how the system works. This can give them the further interests - I think. And if they don’t see that “need”, they have a problem. 

Perhaps I am a bit naive (just read about Launchpad witch I didn’t like, witch surprised me in a negative way). 

But if you read that blog you will understand that the blogger don’t care much about it, like; “I don’t use it”, “have never used it”, “seen it once”, “I like to know how my system works” and so on… 

But; thanks for all your answers!

The things I have read about the work done on Fiesty (the next Ubuntu due out in April) they are not "against" Automatix, but want everything to "just work", so Ubuntu would be ready to go, no need for Automatix. There maybe *people* that do not like it, but you are right, it is good for fixing bug #1, and it is still recomended by some people in the forums.

---

