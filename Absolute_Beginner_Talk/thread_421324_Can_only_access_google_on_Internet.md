---
title: "Can only access google on Internet?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by meinzy on 2007-04-24
Trying to migrate to Linux.  Installed Ubuntu and am able to access Google via the Internet (lan connection).  Any other sites try to load but go no further than the download bar going halfway.  Since I'm able to access Google my network connection is obviously good.  So why can't I access other sites?

---

### Post by n3tfury on 2007-04-24
you didn't say, so i'm going to ask the obvious question.  how did you access this one?

---

### Post by ludatha on 2007-04-24
^ by using another computer

Have you tried a different browser?

---

### Post by tomcheng76 on 2007-04-24
I guess may be dns server setting, but, you can access google, strange...
stupid question: can you ping other website?

---

### Post by n3tfury on 2007-04-24
> **ludatha said:**
> ^ by using another computer

Have you tried a different browser?

be hilarious if he was actually using a different browser on the same PC.   wouldn't it.

---

### Post by meinzy on 2007-04-24
-how did you access this one?-

Opened Firefox, goggled Google, selected Google home page.  Bookmarked and am able to open Google no problem.  When clicking on any other links the download bar goes about halfway and keeps searching until the server finally 'times out'.

I'm a complete and total newbie who has tried Ubuntu once before but got cold feet when trying to deal with all the cryptic, DOS-like commands.  I really want to make the switch but it is not easy.  Got a book but finding time to read and apply it is tough.  I was hoping to at least get the minimums going (Internet & Email) until learning the ins and outs of Linux.

-Have you tried a different browser?-

Nope, don't have one loaded.  I exclusively use Firefox.

-be hilarious if he was actually using a different browser on the same PC. wouldn't it.-

I'm now using Firefox under windows on the same PC with no problems.

---

### Post by meinzy on 2007-04-24
Sorry, didn't mean to repost.

---

### Post by incanus1 on 2007-04-27
I just installed Ubuntu and experience the same problem - I can access only google (and other google service - like picasa, gmail) but I can't access any other site. I can ping other sites (it resolves host to IP).
Any ideas ?

---

### Post by ckempo on 2007-04-28
Same problem here on my sister's PC. Was fine when running Edgy but since the Feisty upgrade, only Google loads.  It's really odd:

[LIST]
[*]Google searches work, but clicking any results just times out when loading the page
[*]All other sites resolve (i.e. ping gives me the correct IP back from the hostname) but I never get a response back
[*]Her ISP ([www.plus.net](www.plus.net)) resolves, and returns ping packets, *but does not load in a browser*
[/LIST]
I can't even update anything - no repository access!

I also notice there seems a similar thread here: [http://ubuntuforums.org/showthread.php?t=424203]("http://ubuntuforums.org/showthread.php?t=424203")

Nothing's changed on the network configuration. Same IP, same router, etc. Can't get my head around it, anyone got any suggestions for the next time I'm at her place? She's "netless" at the minute and isn't very happy...

---

### Post by houstonbofh on 2007-04-28
Wow.  I have been running Feisty on several systems, and have never seen this.  Try some things...  You will need a LiveCD and a USB thumb drive drive.  We will try two states, Installed, and Live-CD.  We will do a lot of the same things in both, and save output to the USB thumb drive so you can post the results.

Start by going to a terminal.  Applications --> Accessories --> Terminal
Change to your desktop.  'cd Desktop'
Get Google. 'wget www.google.com'
Get Ubuntu. 'wget www.ubuntu.com'
Get your config. 'ifconfig -a > ifconfig.txt'

At this point you should have three files.  Save them to a thumb drive in a directory called 'installed'

Now boot the Live CD.  Try a web site.  If it works, do the last command only. If not, do all three and save the results to a directory called 'Live'  Come back and tell us what you have.  There may be more data gathering needed.  If it is a real bug, I can bug it to launchpad, but we need a bit more data.

EDIT: Also look at the post here. [http://ubuntuforums.org/showthread.php?p=2545109#post2545109](http://ubuntuforums.org/showthread.php?p=2545109#post2545109)
If that works, it needs to be bugged on launchpad.

---

