---
title: "Question about permissions"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by OisinT on 2007-09-11
Searched around a little bit for an answer to this one, but can't seem to find the right track.

Basically here's the story:
I recently installed ubuntu on a clean hard drive.  On a DVD I backed up all my bookmarks and contacts from Thunderbird and Firefox on my old computer.
Now, I'm trying to copy the bookmarks etc. from the DVD to the Firefox, Thunderbird, etc. folders.
When I try to do so, however it gives me an error regarding permissions.

An example is:

Error while copying to "/etc/firefox/profile".
You do not have permissions to write to this folder.


I'm sure there is an easy solution. I'm very new to ubuntu obviously so I didn't want to log in as root and screw something up.

Thanks in advance

---

### Post by logos34 on 2007-09-11
To write to /etc you need to use '**sudo** cp ...'.

What about your FF and Tbird files in /home/<user>/.mozilla/firefox/xxxx.default
and /home/<user>/.thunderbird/xxxx.default?

---

### Post by OisinT on 2007-09-11
Well, that's sort of a strange second question for me...
I only have Desktop and Examples folders in /home/<user> at the moment.
In fact, when I tried to install thunderbird by downloading and running the executable file it didn't do anything.  I was only able to install via Synaptic Package Manager

---

### Post by thefowlstar on 2007-09-11
Actually, there are many, many of such "hidden folders" in Ubuntu. To see them, press Ctrl+H in Nautilus.

I personally don't even use Thunderbird, but from what I gather from logos34, you just have to add sudo before whatever command it is that you are typing.

Hope this helps!
thefowlstar

---

### Post by OisinT on 2007-09-11
I see... now that i've gotten that part down, I'm running into other trouble when trying to reinstall plugins, etc.
For example when I want to downloada torrent in azureus, I choose to open with.. but then I can not find the azureus.exe file anywhere on my drive.

---

### Post by logos34 on 2007-09-11
> **OisinT said:**
> I see... now that i've gotten that part down, I'm running into other trouble when trying to reinstall plugins, etc.
For example when I want to downloada torrent in azureus, I choose to open with.. but then I can not find the azureus.exe file anywhere on my drive.

Try 'save...' instead of 'open with'...I think Firefox dumps downloads by default to your desktop.  Then point azureus to the link

---

### Post by OisinT on 2007-09-11
thanks everyone for your help... I think my main problem is (as I'm sure many first time users can relate to) the command structure of how to do things... its not an easy, straight forward drag + drop kind of situation one would be used to in OSX or XP... so thats where a lot of questions come up.
I'm really glad to have somewhere like this where people like myself can have great help from other users with no mean attitudes!
I'm already really happy with my switch to Ubuntu, even if things aren't very easy to figure out.  I've noticed an increase in speed and productivity in my system already - plus the idea of the Add/Remove Applications tool being able to search programmes is genius!
Thanks for all the help... and anyone who wants to be my little (tiny I promise) mentor on ubuntu issues please PM me!!  I promise I wont hassle you with a million messages  :)
just would be nice to have a little instructor here and there for some small issues :P

anyway thanks loads for all the help!

---

