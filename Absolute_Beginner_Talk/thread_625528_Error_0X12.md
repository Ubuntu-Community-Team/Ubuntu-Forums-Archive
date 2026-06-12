---
title: "Error 0X12"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by MoneyGuyBK on 2007-11-28
I have been running Linux SMP in a VM environment for about 2 months now.
When it works and sends a WU, it is great.
But I have had 11 WUs that finished and never reported.  So I have potentially lost over 19K in points.

Here are 2 links where I have posted screen shots of the issue.

I need a Guru's assistance to see if there is something wrong I am missing, and I also need detailed instruction for a how-to fix the problem.

I do thank you in advance.

Peace

Links: See message number 2090 (last one on this page)
[http://www.dellcommunity.com/supportforums/board/message?board.id=Tech_Talk_XPS&message.id=22305&jump=true#M22305](http://www.dellcommunity.com/supportforums/board/message?board.id=Tech_Talk_XPS&message.id=22305&jump=true#M22305)

And:
[http://forums.rampantspeculation.com/viewtopic.php?p=2119#2119](http://forums.rampantspeculation.com/viewtopic.php?p=2119#2119)

---

### Post by rada on 2007-12-01
Hmm.. have never tried running F@H in VM, and since folding-community forum is down can't refer to the posts that solved this for me... but I had that going for a while running natively in Feisty 64 bit. It was either my host name resolution or how I was invoking the client that solved it, but can't remember right now. For a while my network was not set up correctly and folding client was trying to resolve localhost through the internet, so it took too long to resolve.

try pinging your hostname -- for example
```
$ ping myfoldinghost
```

You should get times less than 0.1 ms. If not, make sure your /etc/hosts or whatever you use is configured correctly.

This might also have been one of the errors I was getting when I was starting the client in a console, pausing with *ctrl-z*, and backgrounding the folding job. Instead, now I start the client with

```
$ cd /path/to/my/foldingathome
$ ./fah6 -smp -verbosity 9 > /dev/null 2>&1 &
```

This redirects all standard and error output to nowhere (/dev/null), and seems to prevent a bunch of weird errors I had been getting. To stop the client you can use top, htop, pgrep etc to find the fah6 PID and kill it, or just *killall fah6*

---

