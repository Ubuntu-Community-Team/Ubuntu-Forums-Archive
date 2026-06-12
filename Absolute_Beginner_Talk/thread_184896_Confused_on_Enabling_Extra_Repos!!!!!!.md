---
title: "Confused on Enabling Extra Repos!!!!!!"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-30
I am so confused when it comes to all of the repositories guides.  The ubuntu wiki one seems outdated, as it is for breezy and im using dapper RC now, so I tried the monkeyblog guide but it is different from what the wiki would say, so...

Can anyone just tell me straight up:  Do I just tick all 4 checkboxes (officially supported, restricted copyright, universe, multiverse) for every single repo, or just the binary ones, or what?  BTW, I have the repos from a fresh dapper RC install...if that helps at all...

---

### Post by Sef on 2006-05-30
I just checked them all except for the cd.

What do you find confusing about [Adding Repositories]("https://wiki.ubuntu.com/AddingRepositoriesHowto")?

---

### Post by user1397 on 2006-05-30
[quote=Sef]I just checked them all except for the cd.[/quote]
so you checked all 4 boxes for all repos (binary and source) ?

[quote=Sef]What do you find confusing about [Adding Repositories]("https://wiki.ubuntu.com/AddingRepositoriesHowto")?[/quote]
the part where it says to click the settings button, because that doesn't even show up im my synaptic (i guess its because im using dapper)

---

### Post by steve.horsley on 2006-05-30
Run System->Administration->Synaptic, click Settings->Repositories, Click Add and check all the boxes, then Add, Close.

---

### Post by user1397 on 2006-05-30
[quote=steve.horsley]Run System->Administration->Synaptic, click Settings->Repositories, Click Add and check all the boxes, then Add, Close.[/quote]
okay thanks!
now i have all of my binary repos checked w/ all 4 and my source ones are unchanged. is this correct?

---

### Post by Sef on 2006-05-30
Did you add multiverse to a couple of lines?

---

### Post by user1397 on 2006-05-30
[quote=Sef]Did you add multiverse to a couple of lines?[/quote] srry, but what do you mean by "a couple of lines"???

---

### Post by user1397 on 2006-05-30
i can't believe i cant figure this out!

---

### Post by catlett on 2006-05-30
I think they are going to take you off the green team.:-D 
Just kidding. I think there is a bug. I have the latest Dapper and when I followed those steps the checking off didn't get saved. I did all that but it didn't go into my list. I finally added them by hand.
As you can see I thought I was loosing my mind to. [http://www.ubuntuforums.org/showthread.php?p=1064808#post1064808](http://www.ubuntuforums.org/showthread.php?p=1064808#post1064808)

P.S. I added the extra repos by following the guide in my sig it had a copy of the repositories needed for the restricted stuff and I just copied and pasted. There must be something wrong because there is no way 2 smart guys like us messed up.:D

---

### Post by aysiu on 2006-05-30
This is why the command-line is easier for online help.

It may be easier on one person's end to check and uncheck boxes, but when you're helping someone over the internet, it's a lot easier to say "Paste these commands into a terminal" than to tell someone what boxes to check or not check.

So, follow these instructions, and you'll have the extra repositories:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Forget all that checking and unchecking of boxes for now.

---

### Post by joshrobinson on 2006-05-30
i just always used the ubuntu source-o-matic

[http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

i select dapper, i386 or amd64, country code (US) then check the 2 boxes in the first section, the 2 in the second, and paste it into my /etc/apt/sources.list

---

### Post by user1397 on 2006-05-30
[quote=aysiu]This is why the command-line is easier for online help.

It may be easier on one person's end to check and uncheck boxes, but when you're helping someone over the internet, it's a lot easier to say "Paste these commands into a terminal" than to tell someone what boxes to check or not check.

So, follow these instructions, and you'll have the extra repositories:
[http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources")

Forget all that checking and unchecking of boxes for now.[/quote]
alright, thanks aysiu, i followed the psychocats guide, i didnt get a gpg error, so everything is fine.  So is this the same as allowing multiverse graphically (or thru synaptic)?

---

### Post by aysiu on 2006-05-30
[QUOTE=erik1397]alright, thanks aysiu, i followed the psychocats guide, i didnt get a gpg error, so everything is fine.  So is this the same as allowing multiverse graphically (or thru synaptic)?[/QUOTE] Yes, but it's just harder to give point-and-click instructions over the internet.

If I were standing behind you, I would just say, "Yes, click that, and check those boxes."

---

### Post by user1397 on 2006-05-30
[quote=aysiu]Yes, but it's just harder to give point-and-click instructions over the internet.

If I were standing behind you, I would just say, "Yes, click that, and check those boxes."[/quote]
i understand your point, and thank you so much for providing me with that sources.list --i was going nuts over it! :)

---

