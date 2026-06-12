---
title: "wma files in amaroK"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by ditdu on 2006-07-26
I can't get the amaroK player to auto-detect my wma file tags, it also will not let me edit any of them through the player. Is there any way that this can be done?
Thanks!!!

Edit:
I also found out that once I close amaroK down, it loses all my wma files from the library. I then have to find all the media again! This is very tedious!!!!  :confused:

---

### Post by orb9220 on 2006-07-26
Well I am listening to wma right now. And I don't have alot of wma. You may want to convert them to mp3. But on mine there are Unknown values for length,bitrate,samplerate. But there is Title,Artist,Album,genre in tag info.

Maybe your tags have no info in them. Load an album up then right click edit track info and take a look. If there is nothing there then that might be the problem. Haven't track down this paticular issue since I hate wma and always converted to 192kb mp3's.

Good Luck!

---

### Post by ditdu on 2006-07-26
I have only used wma files because of how easy it was in windows! I dont want to spend hours converting them to MP3 or any other format, as I have quite a lot of them!

I have found out that I cannot edit the tags because of the files not being writable (as they are on the Windows XP partition). Is there a simple way to allow this? (and please make it basic, as I am not used to ubuntu yet!)

Many thanks!!!   :D

---

### Post by orb9220 on 2006-07-26
saw this statement in thread.

"and switch amaroK to the xine engine, you will be able to play .wma, you just won't be able to add the songs to your collection until you figure out how to use the patched libtag."

So there might be a patched lib or some such I'll keep looking.

---

### Post by ditdu on 2006-07-26
yeah, i have them playing fine, so that must be the answer.
When you find it, please tell me! (i will also be looking for it!)
Thankyou very much!
:D

---

### Post by orb9220 on 2006-07-26
are you using amoraK 1.3.9 or 1.4.1?

---

### Post by ditdu on 2006-07-26
1.3.9 i think, thats what i was given when I installed it using the "Add/Remove" function in Applications.
How would I get 1.4.1?

---

### Post by orb9220 on 2006-07-26
open a terminal and enter each of these commands. (Make sure you quit amorak first)

wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)

sudo -s

apt-key add kubuntu-packages-jriddell-key.gpg

echo "deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main" >> /etc/apt/sources.list

apt-get update

apt-get install amarok amarok-engines

Hope this helps because 1.4.1 says

"Metadata support for WMA, MP4/AAC and RealMedia files

As owners of AAC, WMA and RealMedia files found out, tags in such files weren't supported in amaroK 1.3.x series and earlier. As a consequence, these types of files weren't added to the collection and there was no advanced features for them, such as collection search, album covers and statistics. Taglib has since been improved, and these files are now fully supported."

Hope this Helps.

---

### Post by orb9220 on 2006-07-26
Just highlight line copy then paste in term window

---

### Post by orb9220 on 2006-07-26
Don't know if you need to uninstall 139 first?

---

### Post by ditdu on 2006-07-26
I got the following error typing in the first line...

> --00:23:53--  [http://people.ubuntu.com/~jriddell/k...iddell-key.gpg](http://people.ubuntu.com/~jriddell/k...iddell-key.gpg)
           => `k...iddell-key.gpg'
Resolving people.ubuntu.com... 82.211.81.132
Connecting to people.ubuntu.com|82.211.81.132|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
00:23:53 ERROR 404: Not Found.


:confused:

---

### Post by ditdu on 2006-07-26
I know what i did wrong, i put ... instead of the whole page file :)

---

### Post by orb9220 on 2006-07-26
Don't worry about that one I forgot that it did it to me too. That's just the pgp key to verify that it is a valid package.

---

### Post by orb9220 on 2006-07-26
Did it solve yer problem?

---

### Post by McAleead on 2006-08-29
I presume it did indeed sort their problem, as it's sorted out my exact same one. Thanks to you I don't have to lossily re-encode every single WMA track I have in order to hear it on my preferred OS! 

Also, a note on protection for ditdu - if you're storing your music files outside of your home directory, to edit tags you'll need to either grant permission to your user to do so from root or sudo in order to change the tags. You can simply run amarok from the terminal by typing 'sudo amarok' and entering your password. This grants read/write access to files temporarily for maintenance, but 99% of the time you're just going to want to play them. 
Which is useful if you've got multiple users on the same profile (I know, bad habit, but you try exaplining to certain people the benefits of such a system...) or kids, who do insist on finding the delete key hilarious. 

If there's a better way, please tell me how - I'm a bit of a n00b, you see..:D

---

### Post by McAleead on 2006-08-30
Having just managed to render my PC unbootable by playing with my NTFS partitions, I've just redone this procedure. On a fresh dapper install it brought up the error 

[I]The following packages have unmet dependencies.
  amarok: Depends: libifp4 but it is not installable
E: Broken packages
[/I]

But this was fixed by adding libifp4 manually through the package manager. Hope that's helpful if anyone has a similar prob!:)

---

