---
title: "Networking issues/?s"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by DianeHelen on 2008-04-09
Hi again

Well its been a fun day playing with this stuff. For the most part its pretty straightfoward and easy. I got my old Toshiba laptop blazing away, with Ubuntu. I can surf, I can email, I can even IM thru Yahoo and AIM. I can do documents, and pictures, and even drag files across the network from my XP machines to my newly set up Ubuntu/Linux based box.

Here is my current dilemma, and if its as easy a fix as I feel it should be, I will feel quite embarassed. Im not a total idiot, adn have worked with computers and networks for a long time. So, this sorta baffles me.

I searched around adn enabled the Windows Samba networking, and it does see the machines from one to the other.

My head scratcher, is when I try to get to a shared folder on the Ubuntu box, from and XP box, it sees it fine, but throws up a login password prompt, to which I enter the login and password I set up, but it just keeps flashing back as if its not acceptting it.

I went back  to the Ubuntu box, and checked around at some of the permisson stuff, and it all seems just fine. 

But when I try to access a shared resourse, from XP, its a no go.

Any quick ideas what I am missing here?

TIA

Diane

---

### Post by Joe325 on 2008-04-09
When you say "to which I enter the login and password I set up" was this setup via the terminal as:

sudo smbpasswd -a 'A-username'

---

### Post by nickpaton on 2008-04-09
It's probably not working because your firewall is not allowing the XP box to be seen, so have a look [here]("http://ubuntuforums.org/showthread.php?t=202605&page=30#298") on how to install Firestarter the firewall GUI, and set it up.

A simple way to see if it is a firewall problem is to temporarily disable it using Firestarter Disable button on your Ubuntu PC and see if you now have access on the XP PC. 

If you're looking for a straightforward Samba setup look [ here]("http://ubuntuforums.org/showthread.php?t=202605") - used it for years!

Good luck HTH

---

### Post by DianeHelen on 2008-04-09
Umm Have NO idea what THIS IS

sudo smbpasswd -a 'A-username', so cant say..

I just followed the prompts and such for setting up networking..

Its not a Firewall problem, as I can SEE the U box on the XP box. I can Access the U box shares from XP, I can SEE the Ubox from the XP box, but when I double click the U box name (toshibalaptop), I get the login/pw prompt.

Any more ideas to look for?

---

### Post by Joe325 on 2008-04-09
In a terminal , run:

sudo smbpasswd -a 'A-username'    where A-username is a name you create to access the shares. You will then be prompted for a password and then again, to confirm it. Then try to access the share with the username and password you created in the above steps.

---

### Post by DianeHelen on 2008-04-09
Ummm oooooooookk

that actually DID work.

I entered that command string at the terminal prompt on the U box, and it did ask for and confirm a PW.

Now when I try to access the share from the XP box, it lets me right in, withOUT asking for login/Pw. 

Am I correct in assuming, IF I entered the samne name/pw on the termimnal comand on the Ubox, that I just happen to also use, and be logged in with on the XP box,  like regular windows logins, it just passes thru?

Anyway, alot of this is sorta a whole new world to me. (odly its a new OLD world, as I did software instals on Zenix boxes over 20 years ago, when there was no GUI over top. I do remember some of the basic unix commands, but I was never a real expert,.)

Thanks so much for your help.

Now for my next issue, to tackle why I hear no sound..

;), any ideas, since you have been so helpful so far?

:)
Diane

---

### Post by Joe325 on 2008-04-09
Have the basics been checked:

Speaker connection/ power
volume control/ muted


What type of motherboard/ sound card are you using and version of ubuntu?

---

### Post by nickpaton on 2008-04-10
> **DianeHelen said:**
> Ummm oooooooookk
Am I correct in assuming, IF I entered the samne name/pw on the termimnal comand on the Ubox, that I just happen to also use, and be logged in with on the XP box,  like regular windows logins, it just passes thru?

Yes!

By doing the smbpassword bit, you are registering yourself as a user of the network on Ububox.  

Windows (up to XP - don't know Vista) doesn't have any such network 'registration'.

So, because you are already registered on the Ububox, when you access files from XP, XP now doesn't need to ask for any network passwords. 

Brilliant job BTW getting Samba to work.

I haven't read any of your previous posts, but if you want any straightforward background reading and help, check out the[ Psychocats site]("http://www.psychocats.net/ubuntu/").

Good luck!

---

### Post by DianeHelen on 2008-04-10
> **nickpaton said:**
> 
Brilliant job BTW getting Samba to work.






Ya, well no brilliance intended, on my part. Just followed the prompts, and it seemed to work, other than the terminal command part.

Is there any GUI way to have had accomplished that, or is just the nature of this thing, that some things just have to be done via direct terminal command strings? I have no real objection to that, actually its kinda fun, reminds me of the old days, maybe I should even pull out my old  Unix, The basics book. KInda like the old early windows days, when you still really had full DOS underneath, and if you needed to get something done that windows didnt like, you just bi  passed it  and moved stuff, killed stuff, deleted stuff, changed stuff, under the DOS hood.

---

### Post by nickpaton on 2008-04-10
Interesting question that - I thought the answer was 'no' until I googled samba gui and got [this]("http://www.samba.org/samba/GUI/"), so the answer is yes there is - thing is I've never used any of them and don't really feel the need to!

You sound like the orginal Geek (or is that Geekess! ) to me!

As you're probably realising by now, Linux and Ubu are moving more towards the GUI, but there's still a lot which has to be done via the command line, so there's always going to be that feeling of "going where no one has gone before" sort a thing!

---

### Post by DianeHelen on 2008-04-10
> **nickpaton said:**
>  You sound like the orginal Geek (or is that Geekess! ) to me!

 

Yepper! the "original geekESS" for sure..

Ive been "geeking" probably longer than most of you really brilliantly smart guys here, have been breathing..

My first REAL PC, not counting Commodore or Atari, was an an IBM Clone, 8088 XT, running ms DOS  on a 10 MB hard drive. This was the late 70s and I was already out of college.. JUST to really show my age hehehe

I had been working on a TRS III using Ldos, ,and then the PC clones became available, I paid $2500 bucks for the above mentioned 6000000 pound machine :)


But you know what? Those were the days where you HAD to understand what an OS was and what it did, to do anything productive. Once windows drugged the average public, all that was no longer necessary, and as long as you could run a mouse, and click on pretty pictures, you could be a computer operator..

Ahhhhh such is life ey?

---

### Post by nickpaton on 2008-04-10
> **DianeHelen said:**
> Yepper! the "original geekESS" for sure..

Ive been "geeking" probably longer than most of you really brilliantly smart guys here, have been breathing..

My first REAL PC, not counting Commodore or Atari, was an an IBM Clone, 8088 XT, running ms DOS  on a 10 MB hard drive. This was the late 70s and I was already out of college.. JUST to really show my age hehehe

I had been working on a TRS III using Ldos, ,and then the PC clones became available, I paid $2500 bucks for the above mentioned 6000000 pound machine :)


But you know what? Those were the days where you HAD to understand what an OS was and what it did, to do anything productive. Once windows drugged the average public, all that was no longer necessary, and as long as you could run a mouse, and click on pretty pictures, you could be a computer operator..

Ahhhhh such is life ey?

Ah Ha - thought as much!

Just to wet your appetite and bring back some memories have a look at [this little baby]("http://cgi.ebay.com/VINTAGE-VIP-BRAND-XT-8088-COMPUTER-640K-2FLOPPIES-VGA_W0QQitemZ220189863322QQihZ012QQcategoryZ164QQrdZ1QQssPageNameZWD1VQQcmdZViewItemQQ_trksidZp1638Q2em118Q2el1247") - yours for a cool $125 - beats $2500 any day!!

I'm of the Windows drugged mouse era I'm afraid.  But I do have a friend who programs in Linux all day and doesn't even know what a GUI does!!

What I wouldn't give to have my life wound back to those heady dos days and I could have done a proper job instead of fixing other people's Windows and trying to evangelise about Ubu and his friends!

---

