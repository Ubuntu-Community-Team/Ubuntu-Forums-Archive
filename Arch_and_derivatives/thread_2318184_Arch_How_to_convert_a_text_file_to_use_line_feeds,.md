---
title: "Arch How to convert a text file to use line feeds, etc so it can be read in Windows"
date: 2016-03-23
forum: Arch and derivatives
---

### Post by Cavsfan on 2016-03-23
I have been using Arch Linux with just Xfce and mousepad as the text editor for nearly a year now.
But I have yet to figure out how to save text files with Windows line returns, etc at the end of the lines.

I know how to do it in Ubuntu just fine, but any time I save a text file on my USB drive and then copy it into Windows, it's just a single long line.
So, it takes a lot of work to get it like it was in Arch.

Does any one know how to get mousepad to do this?
Any help would be greatly appreciated.
Thanks in advance. :)

---

### Post by Cavsfan on 2016-03-24
This probably holds the key if I can figure out the right command: [https://wiki.archlinux.org/index.php/core_utilities#iconv](https://wiki.archlinux.org/index.php/core_utilities#iconv)

Problem is booting into windows and back to Arch..

---

### Post by QDR06VV9 on 2016-03-24
Not sure i understand fully...maybe >Format. "Word Wrap"
Cavsfan i must confess I just don't use mousepad enough to speak anything relevant.
There is always Nano, Vim, jEdit, Just to point to a few editors that don't pull-in a lot of excess deps..
Sorry Old Friend I was not more helpful.
Kind Regards

---

### Post by Cavsfan on 2016-03-24
> **runrickus said:**
> Not sure i understand fully...maybe >Format. "Word Wrap"
Cavsfan i must confess I just don't use mousepad enough to speak anything relevant.
There is always Nano, Vim, jEdit, Just to point to a few editors that don't pull-in a lot of excess deps..
Sorry Old Friend I was not more helpful.
Kind Regards

Thanks for trying Buddy! I know you probably don't have windows on your machine so you cannot try different things to see if they work.
But, I did solve the problem and the solution was amazingly simple.

At first I thought this would work:
```
iconv -f UTF-8 -t WINDOWS-1251 foo >foo.txt
```
Because once I did that and tried to open it in Arch, it said it was not UTF-8 so it could not read it.
When I switched it to WINDOWS-1251 it looked good but, when I booted into Windows 10, it was still just a single line.

Then I found this simple command:
```
awk 'sub("$", "\r")' foo > foo.txt
```

It worked great! It didn't really change the character format of the text. It just added line feeds, etc. So it could be read in either Arch or Windows 10 with the correct line feeds etc.

I only had to boot into Windows 10 twice, so I only cried for a couple of minutes. :P

Mission accomplished! :popcorn:  :guitar:
I hope someone else can benefit by this thread. Not a whole lot of people that have gone to Arch Linux still also have Windows but I imagine there are a few. 

Kind regards My Friend!

---

