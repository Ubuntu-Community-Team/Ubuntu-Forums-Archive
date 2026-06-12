---
title: "WMV files"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by Ronnie on 2006-10-28
I am new to this and learning as I go.
So can someone explain to me exactly how I got Windows WMV files to play on Edgy?
I have been digging through these forums for four hours now and tried a lot of things that I could never remember.
I found one post that said something about repositorys so I added to them.
How I did that I really don't know. In that same post it listed commands to use in terminal to install different apps. I installed mplayer, gstreamer,amd xine went back to the file and xine will play it.
Does this make any sense???
Also how can I install apps using the gui?
I am handicapped by using Windows all these years but want to move away from that crap.
Please don't laugh at this post I am just a poor newbie trying to not get in over my little head. ](*,)

---

### Post by John.Michael.Kane on 2006-10-28
To install software use synaptic under System--->Administration

as for you wmv issue look here [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats#w32codecs](https://help.ubuntu.com/community/RestrictedFormats#w32codecs)

---

### Post by RudolfMDLT on 2006-10-28
Hi!

See the sound issues link in my sig.

Cheers!

---

### Post by RudolfMDLT on 2006-10-28
Hi Ronnie, For info on wma please read my how to, it pretty good.

Now I hope you read this because I'm pressed for time but I'm gonna explain as well as I can. 

The graphical installer is Synaptic. Click: System => Prefrenses(or administration) => Synaptic. here you search for programs and they magically install. :)

Now how it all works is:

You have your stand alone machine somewhere on this earth. Somewhere else there is a huge pile of software. On your machine you have a sources.list file which basically points Synaptic to this pile of software. You just tick and install. Easy as that.

Now, about the command line, it's a very powerful tool. It makes life much easier for people whom need to help you. n time you will get used to it.

Anyhow,

goodluck!

cheers,


Rudolf

---

### Post by Ronnie on 2006-10-29
> **RudolfMDLT said:**
> Hi Ronnie, For info on wma please read my how to, it pretty good.

Now I hope you read this because I'm pressed for time but I'm gonna explain as well as I can. 

The graphical installer is Synaptic. Click: System => Prefrenses(or administration) => Synaptic. here you search for programs and they magically install. :)

Now how it all works is:

You have your stand alone machine somewhere on this earth. Somewhere else there is a huge pile of software. On your machine you have a sources.list file which basically points Synaptic to this pile of software. You just tick and install. Easy as that.

Now, about the command line, it's a very powerful tool. It makes life much easier for people whom need to help you. n time you will get used to it.

Anyhow,

goodluck!

cheers,


Rudolf

Thanks for y'alls info I found the graphical installer and it works well I really think I am going to like Ubuntu.
I love to learn so I am digging into it's innards:)

---

### Post by Ronnie on 2006-10-29
What is the difference between Synaptic and add/remove on the applications menu?
It appears that Synaptic is OS modules or add ons and add/remove is applications.
Am I right or all wrong?
Thanks y'all

---

### Post by RudolfMDLT on 2006-10-30
Synaptic is basically an interface to the repo's. It will download a catalog of EVERYTHING in the repo's, including app's. It lets you search the catalog for what you need. When it's done it just creates a script file with the text commands for what you want to do. Lets say you ticked w32codecs for install:

sudo apt-get install w32codecs.

The add/remove thing is just Synaptic's pretty little brother.

---

