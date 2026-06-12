---
title: "Trial Software Question - Twonkymedia"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by Quicky on 2007-01-11
I have downloaded some commercial software for Linux, Twonkymedia, which comes as a trial version and apparently runs fully featured for a period of 30 days. Once this period has expired, the software will request a user name and password which can be obtained by paying for the licence.

The program is excellent (streams music, pictures and video to my Xbox 360 flawlessly), and I’ve no doubt that I’ll be purchasing the licence once the trial expires. However, I have been wondering about how the 30 day trial system works (I’m assuming the program will cease to function at the end of the trial).

Since the Twonky program runs within its own folder inside my home folder, what’s preventing me from simply deleting that folder at the end of the trial, and downloading the software again, then extracting it to a new location in my home folder and running it again? Simply, how will the software know if I’ve already downloaded a trial which has expired?

On Windows I would imagine there would be some registry entries, amongst other things, that monitor of this sort of thing but since Twonky is running in my home folder, without root access, how could it keep track of previous trials that have since been removed?

---

### Post by Jussi Kukkonen on 2007-01-11
Well, it could write some *~/.obscurefilename* of course, but I very much doubt it does -- I bet they just depend on your integrity (this is often more effective and always cheaper than depending  on the integrity of a copy-protection system).

---

### Post by Quicky on 2007-01-11
Integrity you say? Highly ambitious.

If it did create some obscure file, it would still have to be somewhere in the home folder though, right? And if I located it, surely I could just delete that also? I’ve never come across any ‘limited trial period’ software on linux before, and was just wondering how they could implement that sort of thing without relying purely on trust. Commendable though it would be.

When I was reading up on Twonky previously, there was a post somewhere on the web from a guy who had an earlier linux trial version of it which, instead of having a 30 day sample licence, lasted indefinitely but only ran for 30 minutes, then terminated. The bloke simply wrote a script that would restart the Twonkymedia server just before it terminated, therefore allowing the program to run continuously.

If exploiting trial software loopholes really is as easy as this, why not just give it to linux users for free? Every other program I use on the platform is.

---

### Post by Jussi Kukkonen on 2007-01-11
> **Quicky said:**
> Integrity you say? Highly ambitious.
Oh no,not even nearly as ambitious as thinking that one could build a technical limitation system that a determined 14 year old couldn't by-pass... 

> If it did create some obscure file, it would still have to be somewhere in the home folder though, right? And if I located it, surely I could just delete that also?
Yes, you could. This is very much like Windows, where you can just remove the use-limiting flags from the registry. 

>  I’ve never come across any ‘limited trial period’ software on linux before, and was just wondering how they could implement that sort of thing without relying purely on trust. Commendable though it would be.

Like I've said, all systems like this rely on trust in the end. It's just a question of how much money you want to spend on trying to make the unauthorized a little more difficult... 

> The bloke simply wrote a script that would restart the Twonkymedia server just before it terminated, therefore allowing the program to run continuously.
There are quite a few free solutions to music streaming (and twonkymedia is not that expensive) and the guy spends his time like that... What a hero.

> If exploiting trial software loopholes really is as easy as this, why not just give it to linux users for free? Every other program I use on the platform is.
Uhh... You can get pretty much any commercial software cracked from the internet. Why won't those companies give the software away for free?

---

### Post by Quicky on 2007-01-11
> There are quite a few free solutions to music streaming (and twonkymedia is not that expensive) and the guy spends his time like that... What a hero.

It was a four-line script – hardly time consuming, and certainly not breaking the terms of the licence. Heroic indeed.

> Uhh... You can get pretty much any commercial software cracked from the internet. Why won't those companies give the software away for free?

You’re missing the point. Cracking is piracy. Deleting the installation folder of software whose trial is over certainly isn’t – that’s called uninstalling. And I’m pretty sure that nowhere in the licence does it give a limit on the number of times you can install the 30 day trial, despite what may be implied. However it isn’t shareware, it’s a commercial product, so I would have assumed that securing revenue for it should have warranted more investment than relying on the honesty of consumers. 

That said, since I’ve still got some time to go before the trial period runs out, I won’t have any more idea of what kind of security they’ve implemented.

> If exploiting trial software loopholes really is as easy as this, why not just give it to linux users for free? Every other program I use on the platform is.

Sarcasm mate. This was just wishful thinking – not something I was expecting to happen. My point is that a large majority of users choose linux because of its open source nature, and the fact that the bulk of available software is 100% free. Yes there are free alternatives to music streaming on linux, but none of them stream music, pictures and video to an Xbox 360. I’m just bitter that it will be the first piece of software I’ll have to buy since migrating to Ubuntu. I thought those days were behind me…

---

### Post by jvc26 on 2007-01-11
Uninstalling the application after the trial is not piracy, going through your computer finding the file which tells the app that the trial is over to stop you installing it again and running the 30 days over an infinite number of times would appear so. After all all a crack does is work its way round the built in protections to stop exploitation. Putting a file somewhere in the computer is a method to stop exploitation is a similar method surely, hence removing that file plays a similar role. The method to keep running by restarting the server before the trial runs out is a form of crack is it not? It just merely circumvents their protection from use without a license - like a keygen or a crack.

Its a shame all software isnt free alas, but by going to Ubuntu at least the huge majority of it is, and you may well find alternatives to the ones which arent. (I havent got any paid software on my computer as its all open source and free) which is one heck of a lot better than the massive investment you'd have to do to set up an XP pc legitimately (And dont even consider the expense for that new mammoth system resource gobbling epic OS which is dawning on our horizons!)

Il

---

### Post by lyceum on 2007-01-11
Even if the program did have something that you couldn't get rid of, all you would need to do is re-install your OS, wiping EVERYTHING clean. There are ways around everything. But if you want them to keep making ugrades to the product, I would recomend paying for it.

---

### Post by Jussi Kukkonen on 2007-01-11
> You&#8217;re missing the point. Cracking is piracy. Deleting the installation folder of software whose trial is over certainly isn&#8217;t &#8211; that&#8217;s called uninstalling.
I assume you are talking about uninstalling and then installing again.

I think you should read your local copyright/contract law* again. In most places the technical methods used to prevent unlicensed use do not matter at all -- If Twonkyvision license says that using the product for more than 30 days is in violation of the license then it very probably is, regardless of any uninstall/install tricks you do...



*) or rather the interpretations of the law -- it's not like this is a case that's defined in any law as such.

---

### Post by Quicky on 2007-01-11
> The method to keep running by restarting the server before the trial runs out is a form of crack is it not? It just merely circumvents their protection from use without a license - like a keygen or a crack.

I don’t think that’s true. All the script did was restart the software – its not circumventing anything, its just running the program – an automatic way of double clicking the icon if you like, which in no way breaks any terms of the licence. Obviously, neither does removing the installation folder after the period of time has expired. Perhaps re-installing the software later on is, but I imagine this would be a difficult claim for the company.

All this is irrelevant anyway, as my original question was of a broader technical nature anyway. I'm not interested in hammering out the whys and wherefores of copyright law. Twonky is just a handy example, since I haven't seen any other similar commercial trials. It was more to do with figuring out what sort of preventative measures software such as this can take to protect exploitation. 

As I understand it, root access in Windows is granted to anything that wants it, so this sort of thing can be hidden away in system files and the registry. This isn’t the case in linux, so essentially I was wondering how trial software would operate in Ubuntu. 

I guess having been a Windows user for so long that I can’t believe it is as simple as creating a date log somewhere in the home folder, or putting faith in the scrupulousness of linux users. Would the software ever have write access to files/folders outside of /home?

---

### Post by Jussi Kukkonen on 2007-01-11
> **Quicky said:**
> Yes there are free alternatives to music streaming on linux, but none of them stream music, pictures and video to an Xbox 360. I’m just bitter that it will be the first piece of software I’ll have to buy since migrating to Ubuntu. I thought those days were behind me…

As a sidenote to the interesting license conversation, it sounds like you have tried or at least compared the different upnp servers. Would you mind telling your experiences or why you couldn't use some of the Free alternatives ?

Some of the possibilities I researched before going with Slim Devices slimserver (a non-upnp server):
*Geexbox uShare
*GMediaserver
*Fuppes
*MediaTomb

---

### Post by Jussi Kukkonen on 2007-01-11
> **Quicky said:**
> As I understand it, root access in Windows is granted to anything that wants it, so this sort of thing can be hidden away in system files and the registry.
That's just not true for any modern version of Windows... Some people do run as administrators all the time, and root-requirement for installers is more accepted, so the end result is the same though.

> I guess having been a Windows user for so long that I can&#8217;t believe it is as simple as creating a date log somewhere in the home folder, or putting faith in the scrupulousness of linux users. Would the software ever have write access to files/folders outside of /home?
If it's not installed as root, then no (except for some special cases like /tmp/). That doesn't really matter though, as hiding a file in your home dir is probably easier than you think (if the software maker really wants to get 'unethical' -- and that has proven to be a bad strategy with linux users): Would you find a newly added gconf key or a file hidden e.g. under ~/.gnome2/ if the name sounds like it's not related to this software ?

---

### Post by Quicky on 2007-01-11
> Would you mind telling your experiences or why you couldn't use some of the Free alternatives ?

Simple really – Twonky is the only one I’ve managed to get working that streams video to the 360. Not only that, but it is updated regularly (an advantage to being a commercial product I suppose) which so far has kept pace with updates to the 360’s firmware. For example a recent MS update, either intentionally or as an effect of some other tweak, prevented some third party upnp servers from streaming video and pictures to it. Within days there was an updated beta version of Twonky which got around this issue.

> would you find a newly added gconf key or a file hidden e.g. under ~/.gnome2/ if the name sounds like it's not related to this software ?

Shouldn’t be too much of a problem if I knew what date my trial software was installed on.

---

### Post by Jussi Kukkonen on 2007-01-11
Aah, video, not audio. I had missed that. I can imagine that serving video is not as easy (especially if the clients change as you told they do).

> Shouldn&#8217;t be too much of a problem if I knew what date my trial software was installed on.
Nope. Changing file creation time is trivial (see *man touch* for example). Once you execute unknown binaries they can do pretty devious things, root or no root.


EDIT I'm getting a little off-topic, but it could be that I was wrong with my touch example -- the inode change time might still be set to the correct time. I'm not sure and don't care enough to test, the point still remains: hiding stuff in a typical home dir is probably not difficult.

---

### Post by Quicky on 2007-01-11
So in your opinion hiding a file somewhere within the home folder is the only method?

---

### Post by konst88 on 2007-01-11
And what about the gconf-editor?
It looks like the registry..
You may write to it with user permitions, and hide there a lot of things.

---

### Post by Jussi Kukkonen on 2007-01-11
gconf is something like registry, but in the end it's just xml files in ~/.gconf/.

Quicky, I do think the home dir is the only way to save information if the program is never given more permissions.

---

### Post by konst88 on 2007-01-11
It is a lot of xml files, which may be very difficult the find the correct one, if it is hidden properly.

---

### Post by psynode on 2008-01-28
Starting up twonky media 4.4.3 with an strace reveals something interesting

First run:
--SNIP--
stat64("/bin/.tv", 0xbfed32e0)          = -1 ENOENT (No such file or directory)
open("/bin/.tv", O_WRONLY|O_CREAT|O_LARGEFILE, 0644) = 13
stat64("/bin/.tv", {st_mode=S_IFREG|0644, st_size=11, ...}) = 0
--SNIP--

Second run:
--SNIP--
stat64("/bin/.tv", {st_mode=S_IFREG|0644, st_size=11, ...}) = 0
stat64("/bin/.tv", {st_mode=S_IFREG|0644, st_size=11, ...}) = 0
--SNIP--


That should be enough info

---

### Post by HornedBeast on 2008-04-24
Seems it doesnt do the above in 4.4.4i.

If only it was a little more stable, I would almost certainly buy this.

Wheres is a FOSS alternative that supports the 360!?

MediaTomb just doesn't do it1

---

### Post by @xi0m on 2008-04-25
Dumb question.  How are you guys configuring Twonky?  When I launch the HTML file in the installation directory it takes me to "http://127.0.0.1:9000/setup.htm" and Firefox say's "Failed to connect".

---

