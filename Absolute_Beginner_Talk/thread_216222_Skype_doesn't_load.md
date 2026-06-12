---
title: "Skype doesn't load"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by Hiroshima on 2006-07-15
I tried the normal version of (Skype Kubuntu Dapper) and the icon just bounced a while and then disappeared. I thought maybe the beta would have better luck starting up, but sadly, not.

Since l lot of people seem to have Skype working, perhaps it isn't a skype question for me but something in the way it is loading...

Any ideas? 

PS, I posted this in the Skype Beta thread, but didn't get any responses, so thought I should try here.

Thank you, Hiroshima

---

### Post by Kobalt on 2006-07-15
How did you install your skype beta version ? Did you compile it yourself ? Try launching it with Alt+F2, just in case your launcher isn't configured well...

---

### Post by Hiroshima on 2006-07-15
> **Kobalt said:**
> How did you install your skype beta version ? Did you compile it yourself ? 
Compile? I'm not sure... this is what I did:
 [LIST]
[*]I downloaded the version for the Ubuntu family (a deb file), 
[*]moved it into the .Skype folder where the old skype was,
[*]opened a terminal
[*]navigated to the .Skype folder
[*]typed dpkg-deb Filename.deb
[*]It gave me some kind of syntax error, and asked if I wanted to install.
[*]I clicked (or typed) yes,
[*]It started (from the script I could see it decompressing and removing the old skype.
[/LIST]

I think it did some or most of the work, because the icon changed colour, and the little bouncing thing beside the pointer changed to blue as well (the original one was brown).

> **Kobalt said:**
> Try launching it with Alt+F2, just in case your launcher isn't configured well...

Ok, DId alt+f2 typed in Skype, and had the same... looked like it was loading, the little pointer bounce was going on , and the bar in the panel said skype, and when I put my mouse over it it says "loading skype"  Then dissapears.

Cheers,

Hiroshima

---

### Post by Drakkor on 2006-07-15
Don't know how you installed it,but you can just go to the skype.com download page and download the installer .deb package ,I have version 1.3beta, then just double click to install. I had problems on a friend's computer trying to install with easyubuntu. :)

---

### Post by jimmygoon on 2006-07-15
NO! Use the repository that they have on the Skype site, and then install from the command line (or Synaptic) with a simple apt-get. Then if you want later you can download the beta and not have to worry about the dependencies.

The reason I said 'NO!' also was so that if you use the repositories, you will get the updates when they come out.

Good luck.

---

### Post by seshomaru samma on 2006-07-15
I have the same problem
try to run 
```
skype 
```
from the terminal and see what you get

btw - do you use SCIM?

---

### Post by Hiroshima on 2006-07-15
> **seshomaru samma said:**
> I have the same problem
try to run 
```
skype 
```
from the terminal and see what you get

Interesting, I get:
[COLOR="Navy"]*** glibc detected *** free(): invalid pointer: 0x08ab7298 ***
Aborted[/COLOR]

> **seshomaru samma said:**
> 
btw - do you use SCIM?

Yes I do. I used UIM in Ubuntu, and now am trying Scim in Kubuntu. It took a while to set up, but now it seems to be working well.  My wife hasn't tried it yet, and that's the real test; to see if a Native Japanese speaker is happy with the input.  The one thing I would like with Scim is a hand drawn imput, for when I don't know the reading of a kanji.  However, that would be for a different thread.


Why, do you use Scim?  

Hiroshima

---

### Post by Hiroshima on 2006-07-15
> **jimmygoon said:**
> NO! Use the repository that they have on the Skype site, and then install from the command line (or Synaptic) with a simple apt-get. Then if you want later you can download the beta and not have to worry about the dependencies.

The reason I said 'NO!' also was so that if you use the repositories, you will get the updates when they come out.

Good luck.

Sorry, that sounds like a good idea, but I don't know how to do it.  Do I add the skype web page as a repository?  In Adept? If you have terminal code for this, it would really help.

[COLOR="Red"]EDIT: Found the answer here:
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)[/COLOR]

Thanks, by the way, to you and everyone who helps us Newbies,

Hiroshima

PS when does one stop being a newbie?

---

### Post by seshomaru samma on 2006-07-15
> **Hiroshima said:**
> Interesting, I get:
[COLOR="Navy"]*** glibc detected *** free(): invalid pointer: 0x08ab7298 ***
Aborted[/COLOR]





Why, do you use Scim?  

Hiroshima

The reason I asked is that it is suspected that Skype and Scim don't go well together.
I use Scim for Chinese and Japanese and I get the same error as you. I tried installing Skype in all sorts of ways , apt-get ,deb files, downloaded from skype.com ,from the repositories and always the same error....

---

### Post by Hiroshima on 2006-07-16
> **seshomaru samma said:**
> The reason I asked is that it is suspected that Skype and Scim don't go well together.
I use Scim for Chinese and Japanese and I get the same error as you. I tried installing Skype in all sorts of ways , apt-get ,deb files, downloaded from skype.com ,from the repositories and always the same error....

Same thing.  I tried installing several ways just now.  I did a search for Skype and Scim, and found several of your posts.

Did you try RUN COMMAND using:

skype --disable-dbus

Or

Skype XMODIFIERS=@im=none QT_IM_MODULE=xim skype

neither worked for me, but they might help you.  I found them on other forums, so you may have seen them already.

---

### Post by TetsuoTW on 2006-07-16
I've got a problem with Skype not loading too. I just tried it in a terminal and this is what I got:
```
tetsuo@tetsuo-desktop: ~$ skype
*** glibc detected *** free(): invalid pointer: 0x08a1c858 ***
Aborted
tetsuo@tetsuo-desktop: ~$
```
Any ideas?

---

### Post by Hiroshima on 2006-07-16
> **TetsuoTW said:**
> I've got a problem with Skype not loading too. I just tried it in a terminal and this is what I got:
```
tetsuo@tetsuo-desktop: ~$ skype
*** glibc detected *** free(): invalid pointer: 0x08a1c858 ***
Aborted
tetsuo@tetsuo-desktop: ~$
```
Any ideas?

Are you using Scim or Skim as well?  That seems to be the source of seshomaru samma and my own problems.  I got the same invalid pointer line when I tried in the terminal as well.

There is a skype page in the wiki
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype) but I couldn't get any of the ideas there or on other forums to work for me (I searched the forums for skype and scim).

Hiroshima

---

### Post by gymsmoke on 2006-07-20
Updating the apt-sources.list with the repo for skype, I was able to install skype without problems, but it will not connect.  Running skype from the command line, there are no errors reported.

Anyone else experience this? I'm running Breezy 5.10

---

### Post by Hiroshima on 2006-07-25
Sorry, no I don't know the answer, I'm just replying so that you know someone saw your post... good luck.

Hiroshima

---

### Post by gymsmoke on 2006-07-25
I found a partial solution - don't bother with the ubuntu version.  remove the repo entries from sources and remove the ubuntu package.  Then go to skype and d/l the beta 1.3 version for linux.  It seems to work fine.

---

### Post by cantormath on 2006-07-25
> **Hiroshima said:**
> Same thing.  I tried installing several ways just now.  I did a search for Skype and Scim, and found several of your posts.

Did you try RUN COMMAND using:

skype --disable-dbus

Or

Skype XMODIFIERS=@im=none QT_IM_MODULE=xim skype

neither worked for me, but they might help you.  I found them on other forums, so you may have seen them already.

Just install automatix
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

it will install it for you.

---

### Post by Hiroshima on 2006-07-31
The solution for the skype skim problem... change to UIM and forget about skim.  You still get Japanese (or whatever language you are using) input, and can open skype.

[http://ubuntuforums.org/showthread.php?t=189834&highlight=scim+setup+japanese](http://ubuntuforums.org/showthread.php?t=189834&highlight=scim+setup+japanese)

This thread shows how to install both Skim and further down UIM.  I changed to UIM without uninstalling SKIM via the instructions there, and it seems to be working well, I can open skype now.

Cheers, Hiroshima

---

