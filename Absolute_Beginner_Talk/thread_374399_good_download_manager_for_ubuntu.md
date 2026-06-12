---
title: "good download manager for ubuntu"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by webofunni on 2007-03-02
Which is the best download manager for ubuntu. Which gives fast download and resume support for low speen dialup connections:)

---

### Post by Paerez on 2007-03-02
Personally I use wget, which is a command line application. You just type:
"wget -c url" and it downloads a file from the url. The -c means continue, so it will resume.

If you don't like the terminal, there is [gwget]("http://www.gnome.org/projects/gwget/index.html"). It's in the repos.

---

### Post by steve101101 on 2007-03-02
i either use synaptic or aptitude from the terminal

---

### Post by Perfect Storm on 2007-03-02
If you are not into commands (yet), I suggest trying D4X.

---

### Post by webofunni on 2007-03-02
comparing with dap or fdm in windows i find gwget and freeloader is bit down what you think ? Also give me some offline dictionaries in english like wordweb in windows. Now i am using ww with wine is there any linux alternative

---

### Post by Paerez on 2007-03-02
I don't know about offline dictionaries. I always have internet, so [www.ninjawords.com](www.ninjawords.com)

---

### Post by jkeyes0 on 2007-03-02
It's kinda sad to say, but I use DownThemAll, a firefox addon.

[https://addons.mozilla.org/firefox/201/](https://addons.mozilla.org/firefox/201/)

---

### Post by kerry_s on 2007-03-02
I use prozilla. I've tried others but i like prozilla best, it's simple, small and fast.

For gui command> xterm -T "PROZILLA" -e dproz
To replace wget and make any app that uses wget fly(dillo,...)->
sudo su
mv /usr/bin/wget /usr/bin/wget1
ln -s /usr/bin/proz /usr/bin/wget

I also use axel when i do server installs, but it doesn't seem as fast as prozilla. It's just a heck of alot faster than straight wget when installing from the net.
Note you can still use the real "wget" just use "wget1".

---

### Post by webofunni on 2007-03-03
Yes i also relay on downthemall firefox extension it act as a good download manager. Still i dont get answer for a good offline dictionary

---

### Post by vnt87 on 2007-03-04
Most download manager in Windows (like IDM, FlashGet, HiDownload etc.) has the 'drop target' feature. It's a small floating windows that stays in the corner of your screen, you can just drag and drop URLs into it and it's added to the download manager's queue. That's one of the feature I miss when moving to Linux.
Is there a download manager in Linux that has similar feature? Currently I use freeloader, it has good speed and you can drag and drop links in it, but it doesn't stay on top, plus it doesn't look like it can resume broken download.

---

### Post by Paerez on 2007-03-04
You know you can right click any window in the window manager bar and click "On Top" to make it stay on top?

---

### Post by vnt87 on 2007-03-05
> **Paerez said:**
> You know you can right click any window in the window manager bar and click "On Top" to make it stay on top?

Of course but the windows are kinda big, unlike the tiny little drop spot in IDM or FlashGet. I could resize the windows, but that's not the same as having a separate drop zone, it's more convenience. That's why most (if not all) download managers in Win$ support it.

---

### Post by Paerez on 2007-03-05
ah ok I got it.

Why do you guys need download managers anyways? I only download a file or two at a time, and firefox does it for me.

Even for the ubuntu isos I dont need all that functionality....

My of my download managing for big files is bittorrent anyways.

---

### Post by webofunni on 2007-03-05
but a download manager is necessary for people like me with ever breaking slow dialup connections. it will be better if free download mangers like fdm release a linux version. also is there any idea about a offline dictionary

---

### Post by Paerez on 2007-03-10
as for offline dictionaries, isn't there the one under "Applications->Accessories->Dictionary"?

---

### Post by msak007 on 2007-03-10
> **vnt87 said:**
> Most download manager in Windows (like IDM, FlashGet, HiDownload etc.) has the 'drop target' feature. It's a small floating windows that stays in the corner of your screen, you can just drag and drop URLs into it and it's added to the download manager's queue. That's one of the feature I miss when moving to Linux.
Is there a download manager in Linux that has similar feature? Currently I use freeloader, it has good speed and you can drag and drop links in it, but it doesn't stay on top, plus it doesn't look like it can resume broken download.
I'm on Kubuntu, so I use KGet in conjunction with Firefox and the [FlashGot]("https://addons.mozilla.org/firefox/220/") extension. KGet has a drop target feature like you're looking for so you can drag links to it manually (screenshots attached).

---

### Post by dreadlord_chris on 2007-03-14
OK, I've tried all the suggested DL managers - plus a few more besides. So far none seem to have the one feature I'm loking for. I have a feeling wget will do what I want - which would be fine, the command-line doesn't scare me :tongue: - I just can't for the life of me figure out what the command-line would be.

I want to be able to grab only certain files from a web site. For instance, all the flacs from this site:
[http://ia340903.us.archive.org/0/items/glove2006-10-29.482flac16/](http://ia340903.us.archive.org/0/items/glove2006-10-29.482flac16/)

If someone knows what the wget line would be - or point me to an app that can selectively download - I would be eternally grateful....

---

### Post by kpkeerthi on 2007-03-14
```

wget -r -v -A *.flac http://ia340903.us.archive.org/0/items/glove2006-10-29.482flac16/

```

---

### Post by dreadlord_chris on 2007-03-14
> **kpkeerthi said:**
> ```

wget -r -v -A *.flac http://ia340903.us.archive.org/0/items/glove2006-10-29.482flac16/

```

Well, that didn't work - I ended up with a robot.txt file that disallowed access to all robots/spiders...
Thankfully they also have ftp access

```

wget -r -v -A flac ftp://ia340903.us.archive.org/0/items/glove2006-10-29.482flac16/

```

works like a charm though...

p.s. I had to change the switch *-A flac* since _-A *.flac_ errored out on me....

Thanks for pointing me in the right direction though - it was the -r (recursive) that I wasn't getting. Recursive downloading sounded more like sucking the whole site, parent directories & all....

makes sense now though \\:D/

---

### Post by kpkeerthi on 2007-03-14
Glad it worked. I was typing that command from my windows machine in office. Haven't had a chance to validate that the command works 'perfectly' fine.

---

### Post by msak007 on 2007-03-14
> **dreadlord_chris said:**
> OK, I've tried all the suggested DL managers - plus a few more besides. So far none seem to have the one feature I'm loking for. 
KGet's drop basket wasn't what you were looking for? I mean wget is the easiest route to go if you know the URL of the file so it's cool that's workin for you, but I'm just curious as to what other features you were lookin for that none of the DL managers had.

---

### Post by dreadlord_chris on 2007-03-15
> **msak007 said:**
> KGet's drop basket wasn't what you were looking for? I mean wget is the easiest route to go if you know the URL of the file so it's cool that's workin for you, but I'm just curious as to what other features you were lookin for that none of the DL managers had.

What I want/ed is/was a dl manager that I can enter a base URL (to the folder containing the files I want), and download only the files I specify through a filter or search string.

i.e.  [http://baseurl.com/to/some/folder/](http://baseurl.com/to/some/folder/)
       filter=.flac

the dl manager I'm looking for would then connect to [http://baseurl.com/to/some/folder/](http://baseurl.com/to/some/folder/) and download ALL files that match the filter....

Drop-targets (KGet/D4X/Whatever) aren't what I'm looking for. I'm mainly using this for downloading live shows from [Live Music Archive]("http://www.archive.org/details/etree"). Many of these shows will have 20+ tracks to download. With any of the dl managers I've found, I would have to enter (dragNdrop/click) each individual track - rather inefficiant...

Oh ya, and I use Opera for browsing - so drop-targets don't really worjk for me anyway....

---

### Post by blogmaster on 2007-05-24
is there anyone who can help me installing prozilla??? i simply can't install that... i downloaded the tarball (deb is not available)... and after unpacking, i run all the instruction given on prozilla site but after running ./configure, it shows me loadsa error (something like several gawk, cpp, c++, gp and many others are not available) but when i installed all those (not exactly all, since all are not on Synaptic package manager, only 2 or 3 were left)... so please help me, those who has successfully installed prozilla please help me... i am on ubuntu 7.04... detailed instruction is welcomed...

---

