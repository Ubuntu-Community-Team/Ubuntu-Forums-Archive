---
title: "How can I reduce the Download Bandwith?"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-06-07
Hello All!

I would like to ask the following:

When I try to download something (e.g. a Big file), I end up NOT being able to load/browse other Internet Pages in the Web (using my Mozilla Firefox)...

... until my download is finished... & my Web Browsing ability is restored...

Is there a way to limit the Download Bandwith, so that there is always some space left for some Web Browsing during a download process?

Thanks.

P.S.> Sorry, but it is "damn" boring when you are downloading & you can't Surf in the meantime...

---

### Post by giftnudel on 2006-06-08
Hi,

yes indeed there is an option, it involves using the commandline:

Assume you want to limit to 23 Kbytes (or 1 Mbyte) per second:

1. open a terminal
2. type wget --limit-rate=23k (or --limit-rate=1M)
3. copy the link from which you download to the terminal so that you see in total
```
wget --limit-rate=23k http://some.server.with/some/file
```

you might want to look at the help of wget (type 'man wget' in a terminal) for more sophisticated options.

regards, 
giftnudel

---

### Post by dvarsam on 2006-06-08
Dear "giftnudel",

Thanks for your reply!

> Yes, there is an option.
It involves using the commandline:

Assume you want to limit to 23 Kbytes (or 1 Mbyte) per second:

1. Open a terminal

2. Type ```
wget --limit-rate=23k (or --limit-rate=1M)
```

3. Copy the link from which you download to the terminal so that you see in total
```
wget --limit-rate=23k http://some.server.with/some/file
```

You might want to look at the help of wget (type 'man wget' in a terminal) for more sophisticated options.

_Questions_:

1. I have a DSL 384 connection speed.
    What would the appropriate value be for "--limit-rate=??k"?
    (Example: "...=370k", "=360k" - what value?)

2. When I download stuff from the Internet (e.g. a package using the Synaptic Package Manager's program), the approach I use to Download a file (in such a case), is through a GUI...
Is there a "hidden" option somewhere deep in the GUI (a window) where I can limit the Download speed NOT only for a single download, but for _ALL_ future ones too?

Thanks.

P.S.1> I hate having to do this again&again every time I want to download a single file - I want to perform this once & be set for ALL future downloads...!!!
P.S.2> It is also boring if you can NOT surf while a package is in a download proccess!

---

### Post by giftnudel on 2006-06-10
Hi,

I'm sorry, the option I told you is only possible if you want to download one or more big files in the terminal. You can add something to your .wgetrc (I think, not sure!) and it then works for all your future downloads with wget in the terminal. I think (again, not sure) that adding something like limit-rate=30K to ~/.wgetrc should do.

As for your connection speed, this is 384 Kbits (bits not bytes) and wget wants bytes, if you know (well now you will) that 8 bits = 1 byte, just calculate 384 / 8 = 48 Kbytes per second. This is your maximum connection speed. I suggest to take off >8 Kbytes  so you will end up with --limit-rate=40K or less (may be better)

As for the system wide control I suggest you file a wishlist bug at bugs.ubuntu.com in the component gnome-session where you request such a feature, it actually is a nice idea! (note that gnome-session may not be the best choice but I don't know a better one)

If you have more questions, just ask.

regards,
giftnudel

---

### Post by dvarsam on 2006-06-11
Dear "giftnudel",

Thank you for your repply!

> You can add something to your .wgetrc (I think, not sure!) and it then works for all your future downloads with wget in the terminal.

I think (again, not sure) that adding something like limit-rate=30K to ~/.wgetrc should do.

Ok, I performed an ```
locate wgetrc[/quote]

And located "wgetrc", under "/etc/wgetrc"...

So, you are suggesting that a command like [code]--limit-rate=40k
```, is going to do the trick?

And on which line (or where exactly) should I add the above command?
(cause 1rst thing is to do it & 2nd to verify whether it has been done - I have NO clue how to go on either of these...)

> As for the System Wide Control I suggest you file a wishlist bug at bugs.ubuntu.com in the component gnome-session where you request such a feature, it actually is a nice idea! (note that gnome-session may not be the best choice but I don't know a better one)

So I guess that I can NOT make this work, "Systemwide" (to also work on Downloads performed through Synaptic or Firefox)...

It is SAD that the Ubuntu Programmeers have never thought of that...:confused:

---

### Post by giftnudel on 2006-06-13
Hi,
wait, you can try to add limit-rate=40k to this file (at the end) and that should work for synaptic (since it uses wget)

Please report back if this works

giftnudel

---

### Post by dvarsam on 2006-06-16
> You can try to add limit-rate=40k to this file (at the end) and that should work for synaptic (since it uses wget)

Please report back if this works

Dear "giftnudel",

Thanks for your suggestion!

I tried this today - since 70 more updates appeared for my Ubuntu Dapper!!!

I thought that it was the perfect opportunity to test what you suggested!

From days before, I had performed a "nano /etc/wgetrc" & had added in the end a line with" limit-rate=40k", as you had previously suggested!

And this was the time to test if this will work!!!

I supposed that having 8k remaining for the rest of the applications during the download of updates (...you said that my DSL 384 speed should provide 48k data speed!..., so, limiting my downloads to 40k should leave 8k for browsing/surfing...), should be enough for my Internet browsing/surfing needs...

However, this 8k seemed not enough for browsing...!!!

I could still _not_ browse!!!

I went & reduced it from 40k to 35k!

However, when I resumed the downloading process, the downloads would _exceed_ the 35k limit I applied...?

I thought that this was because I did NOT _force_ a Restart for the new settings/limits to apply!

Since I did not know how to "restart"/reload the new settings, I decided to Restart the Ubuntu PC!

After a Restart, I resumed the downloading (this time at 35k) & I should have 13k left for all other jobs (e.g. browsing the net)...

The downloading was _indeed_ limited to 35k, however the remaining 13k could _not_ be utilized for any other jobs (e.g. browsing)...

No Internet browsing/surfing was possible!!!

So, therefore, I have to assume that:

> Adding an upper "limit" to the "wgetrc" file, limits the _whole_ PC to this speed & _unfortunately_ it is NOT possible (under such circumstances) to _use/utilize_ the remaining/freed bandwith for any other purposes (e.g. browsing the Net).

_Outcome_:
The Bandwinth dedicated for Downloading is Decreased & the "Freed" Bandwith can NOT be utilized by any other applications that use the Internet!!!

Of course, this is very bad, because _NOBODY_ likes his downloading processes to use/hijack the _whole_ bandwith & to NOT be able to browse during a download proccess!!!

I hope the Ubuntu Programmers fix this, cause it seem to me that this is an _awful_ approach on the downloading of applications/upgrades!!!

It is as if my PC is keeping me as a "hostage" (since I have NO Internet), until the download is finished!!!

Thanks.

P.S.> IF anybody has a solution to this, please provide, cause this is TOTALLY ridiculous!!!:confused:

---

### Post by giftnudel on 2006-06-20
Hi,

funny enough, I don't really understand that completely. I have seen, that synaptic downloads 2 files simultaneously so you have 35K x 2 = 70 K >> 48K and that might not have done it. I think that there is a configuration file for apt which should be able to control that (including a limit) so you might want to look at that. 
I know from experience that wget --limit-rate + browsing works without any problem, so I suppose the problem is really that it tries to download 2 files simultaneously.

If you have any other ideas, please tell me

giftnudel

---

### Post by editrix on 2006-06-21
dvarsam, are you sure the bandwidth is the problem? I ask because I'm on dialup, and if I download using apt-get in the terminal, I have no problem surfing, but if I'm using Opera to download (say, a music file) then I go wash dishes or something until the download's finished.

---

### Post by dvarsam on 2006-06-21
Dear "editrix",

Thanks for your reply!

[QUOTE=editrix]dvarsam, are you sure the bandwidth is the problem?
I ask because I'm on dialup, and if I download using apt-get in the terminal, I have no problem surfing, but if I'm using Opera to download (say, a music file) then I go wash dishes or something until the download's finished.[/QUOTE]

Well, to be exact, I do not know whether the bandwith is the problem...

However, I can think of nothing else...

All I can say, is that I use Firefox v1.5.0.4, and perform my downloads from there or from/using the "Synaptic Package Manager" (when I download software packages or do an OS "everyday" upgrade)...

On _both_ situations, during a download (or when a download is in progress), I can NOT surf the net!

Is this feature supposed to be called "multithreading or multitasking"?

Maybe Ubuntu's Synaptic & Firefox do not have this capability... do they?

Thanks.

P.S.> If you have some other idea, or _if_ I need to provide more feedback, please tell me what to do/what you want me to do...

---

### Post by editrix on 2006-06-21
[QUOTE=dvarsam]P.S.> If you have some other idea, or _if_ I need to provide more feedback, please tell me what to do/what you want me to do...[/QUOTE]

All I can suggest is you find some program you're curious to try anyway (games are always good :wink:) and download/install it from the command line: 

sudo apt-get install <name of program>

It should be big enough to give you a chance to test your browser. 

I have no idea why, but using command line always seems faster to me.

---

