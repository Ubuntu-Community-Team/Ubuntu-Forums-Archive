---
title: "What's a good Usenet binary reader?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by MartyNg on 2007-06-19
Hello. I have been using Ubuntu 7.04 for a few weeks and am loving it. One of the few things I still use my Windows box for is for Usenet binary downloading. I have a program called Newsbin that works really good. Can anyone recommend a program that runs well in 7.04? It must be able to decode binaries. (Unless someone can help me out of my indie music obsession!)  Thanks!

---

### Post by Sonofmoog on 2007-06-19
My best recommendation is to install Wine, if you haven't, and run Forte Agent.  There is no newsreader on the planet in *any *OS as good at handling binaries.

You might consider subscribing to a news service that provides access to the binary newgroups through your browser.  Newsguy is one; there are many others.

---

### Post by dronepower on 2007-06-22
newsbin version 4 will run ok with wine.

the newbin programmers are working on  linux version i heard.

---

### Post by kwacka on 2007-06-22
I'll assume you don't want to read the headers etc, so try klibido.

For reading usenet forum try pan, not quite as 'feature rich' as agent, but its on the way. You can also use it for nzbs - under file there's "import"

Both are available in repository so a simple sudo apt-get install pan klibido will get you running.   Add par2 for par files (runs from command line e.g. par2repair *.par2)

Also take a look at  hellanzb - one of the best around when you've got it set up. If all files are there it doesn't download par2 files, and will automatically run unrar, par2 if required.

---

### Post by PhatStreet on 2007-06-22
If you're only downloading binaries and not reading any articles, I've found that hellanzb is incredibly easy to use once set up.

---

### Post by JimNSB on 2007-06-24
I can use Agent!?! Great news!  I "*paid my $29*" and have been using Agent for mail & NG's for over a decade.

I just started with Ubuntu this weekend, installing it on a new, separate system. Is there a way to 'move' my Agent installation from my Win2k system to this new Ubuntu box, similar to how I moved it onto new Windows systems?  I'm guessing the NFTS FS the files are on now is going to be the tricky part.

---

### Post by Sonofmoog on 2007-06-25
> **JimNSB said:**
> I can use Agent!?! Great news!   .. Is there a way to 'move' my Agent installation from my Win2k system to this new Ubuntu box, similar to how I moved it onto new Windows systems?  I'm guessing the NFTS FS the files are on now is going to be the tricky part.

Yes, you can move your Agent installation to your Ubuntu system.  If you are networked, just copy them over, and put them wherever you want.  Make sure that a copy of agent,ini is in fake_windows, and in the directory where Agent.exe is located.  

The only caveat I would add to all this is my experience with Agent under Wine is limited to versions 1.xx, and I had no problems.   I can offer you no assurances that later versions of Agent will run as well.

---

### Post by MartyNg on 2007-06-25
I was talking to some guys in class, and they were raving about NewsLeecher. Has anyoneo got this program to work under WINE? I've tried it, but only get a messed-up window that I have to force close.

Thanks!

---

### Post by alienexplorers on 2007-06-25
Have you given PAN newsreader a try.  It's in synaptic and works great for me.

---

### Post by RaiSuli on 2007-06-25
Hellanzb and Pan = the first for downloading with nzb files, the second for reading and posting. Klibido crashed on my system when updating very large groups. Newsbin is also a great program, if you'd rather run something in Wine. Check out the Newsbin forums' linux section. There's some good advice there.

---

### Post by qpieus on 2007-06-25
> **Sonofmoog said:**
> 
The only caveat I would add to all this is my experience with Agent under Wine is limited to versions 1.xx, and I had no problems.   I can offer you no assurances that later versions of Agent will run as well.

Version 3.3 works very well under wine. v4.0 and above don't work well - sometimes the program starts, sometimes not, memory fault errors, it's generally unreliable.

---

