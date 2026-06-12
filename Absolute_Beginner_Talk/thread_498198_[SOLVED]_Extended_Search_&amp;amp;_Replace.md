---
title: "[SOLVED] Extended Search &amp;amp; Replace?"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-07-11
(aka: Please help me stop booting Windows to get things done! ;) )

I need multi-line search & replace for HTML files - within a single document, within all open documents, and within a project.

I haven't found this function on Linux at all yet - not Bluefish, not Quanta Plus, not Gedit, etc-etc. Is it there somewhere and I can't find it?

---

### Post by KIAaze on 2007-07-11
For powerful search and replace using regular expressions I suggest **Kate**. :)

Now to replace over a whole group of files, I don't know if there's a direct command, but it's fairly easy to script.

With this command:
```
sed s/<pattern A>/<pattern B>/g file
```
you can replace all words in file matching pattern A with pattern B.

This command itself will not touch the contents of the file. It will only print out the resulting text.

To change the contents of the file, use the "-i" option:
```
sed -i s/<pattern A>/<pattern B>/g file
```

Here are some already made scripts you can use:
[http://tips.webdesign10.com/recursively-find-and-replace-linux]("http://tips.webdesign10.com/recursively-find-and-replace-linux")
[http://linuxphile.org/node/13]("http://linuxphile.org/node/13")
[http://www.student.northpark.edu/pemente/sed/sedfaq4.html]("http://www.student.northpark.edu/pemente/sed/sedfaq4.html")

And a function available in the mysql-server-5.0 package:
[http://www.hmug.org/man/1/replace.php]("http://www.hmug.org/man/1/replace.php")

Note that in Kate you can add scripts or programs as functions in "Settings->Configure Kate->External tools". :)

The two most famous text editors emacs/xemacs and Vim also feature the possibility of adding plugins and  I'm quite sure that such plugins must already be available for them.
The problem is that I don't know them well enough. They take some time to master.

If you are interested in writing scripts for text treatment, look for:
-tr
-grep
-sed
-awk
-perl

All of them are available as commands, but the last 3 even have their own programming language.
They are listed here from easiest to most difficult (but also simplest to most powerful).

grep and sed I use pretty often. awk I know a little about. (command-line only usage for all)
Perl I can't understand at all. ^^

---

### Post by Inxsible on 2007-07-11
I dont know if this is what you want, but by using an IDE like Eclipse or NetBeans for HTML editing, you will get not only the search and replace functions, but a lot many neat functionalities too

---

### Post by ofb on 2007-07-11
Have a look at the attached image for what I'm describing. 

You just highlight the target, click, and type/paste in the replacement. It's very fast, and I use it constantly.

Looking at the online docs, Eclipse and NetBeans seem to have only the single-line search & replace dialog that the other Linux editors have. If they do have what I'm showing, then please tell me. I'll adapt to a new IDE if that's the only way to have this function in Linux.

---

### Post by KIAaze on 2007-07-12
Maybe this list can help you:
[http://en.wikipedia.org/wiki/Comparison_of_text_editors#Extra_features]("http://en.wikipedia.org/wiki/Comparison_of_text_editors#Extra_features")
(Look at the multi-line regex column.)

Otherwise I think it should be posted as a feature request for Gutsy (or Bluefish).

I'm sure that any programmer with enough experience in text treatment can program this quite quickly.

Here's an example of what Perl can do:
[http://ubuntuforums.org/showthread.php?t=487551]("http://ubuntuforums.org/showthread.php?t=487551")

Try asking on the Bluefish mailing-list.
Maybe such a feature is already available in the development version or is planned.

---

### Post by ofb on 2007-07-12
> **KIAaze said:**
> Otherwise I think it should be posted as a feature request for Gutsy (or Bluefish).

It's been requested before. Funny that Bluefish doesn't have it, because that app is clearly influenced by Homesite users.

Bluefish-unstable is listed as having "improved search and replace" but I can't find a detailed description. (I did download the rpm, converted it to deb & installed, but I kept running into dependency issues so backed off. I'm posting in "Absolute Beginners" for good reason, after all.)

> I'm sure that any programmer with enough experience in text treatment can program this quite quickly.

Yes, that was what I thought. Hours of Google later, I'm getting the idea that only Homesite really had this, which is quite astonishing after nine years. I've posted the question to the forum here because I really can't believe that's the right conclusion.

Nick Bradbury is adding the feature to the new TopStyle, but Win only, alas.
[http://nick.typepad.com/blog/2007/06/extended_replac.html](http://nick.typepad.com/blog/2007/06/extended_replac.html)

I should add that I do appreciate that you're trying to help with the regex advice, but learning and remembering regex while composing HTML/CSS that works across our browsers is a little more than I can carry in my head. I need the GUI.

---

### Post by KIAaze on 2007-07-13
What dependency issues? I might be able to help you with that.

If it's an unstable package, it might be even easier to install it from source. (gives clearer error messages (to me at least))
I think I'll try it out this weekend.

Otherwise, I'd be glad to create such a program myself. :)
The GUI wouldn't be such a big problem, but I still have to master regex treatment, either in C++ with the boost::regex libraries or with Perl (which I currently don't know at all).
Unfortunately, I don't think I'll be able to do it before October because of time issues.

---

### Post by ofb on 2007-07-13
> **KIAaze said:**
> What dependency issues? 

Oh geez... from memory? I think the first one was a perl lib. I googled it + "ubuntu" and found other people with the problem, and followed somebody's CLI commands that I think redirect the request to a lib that Ubuntu has that is equivalent? Then I got a second missing-file type error for I believe another perl item, and I decided to back off -- I really don't want to accidently mess up my machine (again), and I only wanted to check Bluefish-unstable to see if the 'improved' search & replace meant extended. Good chance it doesn't, and I'll find out in a few months when 1.1.3 goes stable anyhow.

> Otherwise, I'd be glad to create such a program myself. :)
The GUI wouldn't be such a big problem, but I still have to master regex treatment, either in C++ with the boost::regex libraries or with Perl (which I currently don't know at all).
Unfortunately, I don't think I'll be able to do it before October because of time issues.

Well, google a bit for "extended search and replace" and I think you'll see people really like that feature. For them, and me, it's the killer item that keeps them with Homesite. So if you want a project that would be very appreciated, making a Homesite-style Search & Replace for one of the Linux editors would be a good candidate. It's definitely one of two final items to that keep me booting Win.

If you've got any questions about how the Homesite one functions, just ask, but I think everything it does is in that screenshot.

This should be an opportunity to do it better of course, but truth is I can't think of any improvements to make

---

### Post by KIAaze on 2007-07-30
Good news everyone! :)

I found a python script that can replaces multiple-line patterns in multiple files recursively!
Here it is:
[http://xahlee.org/perl-python/find_replace_dir2.html]("http://xahlee.org/perl-python/find_replace_dir2.html")

The guy's webpage is very interesting by the way. ;)

```

#! /usr/bin/python
# -*- coding: utf-8 -*-

import os,sys

mydir= '/Users/t/web/x'

findStr='''<body>

<table>'''
repStr='''<body>\n<P>new stuff!</p>\n<table>
blabla'''


def replaceStringInFile(findStr,repStr,filePath):
   "replaces all findStr by repStr in file filePath"
   tempName=filePath+'~~~'
   input = open(filePath)
   output = open(tempName,'w')

   s=input.read()
   output.write(s.replace(findStr,repStr))
   output.close()
   input.close()
   os.rename(tempName,filePath)
   print filePath

def myfun(dummy, dirr, filess):
    for child in filess:
        if '.html' == os.path.splitext(child)[1] and os.path.isfile(dirr+'/'+child):
            replaceStringInFile(findStr,repStr,dirr+'/'+child)
os.path.walk(mydir, myfun, 3)

```

This script searches recursively in "mydir" for files ending in .html and replaces "findStr" with "repStr". Change variables as needed.

Now, all that's needed is a nice PyGTK interface and a way to use it by command-line. :)

Creating a plugin for Kate will then be extremely easy. (see Settings->Configure Kate->External tools)

I also started learning Perl, but now that I found this...
I might as well learn Python right away. :roll:
I also found out how to replace multiple lines in sed, but unfortunately it only works for 2 lines so far:
```
sed '/hello/N;s/hello\nworld/hi\nmama/' toto.txt
```
This will transform:
> hello
world
i
am
toto

into:
> hi
mama
i
am
toto

source: [http://www.computing.net/unix/wwwboard/forum/6593.html]("http://www.computing.net/unix/wwwboard/forum/6593.html")

---

### Post by ofb on 2007-08-14
Back to GUIs, I have found one Linux HTML editor with extended search & replace.

[http://en.openwebsuite.org/](http://en.openwebsuite.org/)

Alas, it's not really a Linux program, but is a standalone app that runs on Java. This means it does not act quite like other programs, which rapidly becomes plain annoying as you try to get tasks done. 

Quick example - you can't scroll across options with the mousewheel, and the doubleclick rate is set so high that I ended up stabbing out triple- and quad-clicks just to open files. The overall difference in "look & feel" is rather more than the difference between say Ubuntu and W95, or OS8.

That said, this is a recently GPL'd project - perhaps some aspects of its extended S&R GUI code will be helpful to people working on the established Linux editors.

---

### Post by ofb on 2007-08-24
Well this is kind of crazy, but Bluefish and Quanta (with KFileReplace) do in fact have multi-line search and replace, though it's sure not obvious, or apparently well known.

The trick is /pasting/ your multi-line target and replacement into the single-line forms. If you try typing, hitting the Enter key for a line-break submits the S&R of course...

While I'm relieved that multi-line search & replace does exist in Linux, it needs work. Aside from the extra steps mentioned above, neither works across projects. KfileReplace does directories, with or without subdirectories. Bluefish doesn't have that option, but does offer the option of all open documents instead.

What's wanted is the choices Homesite had ten years ago:
-current document
-all open documents
-in folder (with subfolder option)
-in project

And of course, use full-size full-function multi-line entry forms, and place the original highlighted text in the Search portion automatically.

That might sound like quibbling, but it really does add up when you do a lot of HTML. So, I dunno. I'm going to play with both editors more to see if I can adapt, or learn how to use their methods faster, but it does look like I'll still be booting Windows to get things done. Which is a darn shame, as I've become very happy with Linux for everything else now.

---

### Post by KIAaze on 2007-08-26
I just tried KFileReplace.
When you double-click on a created search/replace action, it opens a window where you have two text boxes in which you can type the text to search/replace.

[IMG]http://img339.imageshack.us/img339/597/screenshotinsertsearchioq4.png[/IMG]

Unfortunately, pasting multiline text into the box doesn't seem to work. You have to type the text hitting enter as necessary to make it actually find the text. :(

I guess it has something to do with the way newline characters are pasted into the textbox.

Other than that it seems quite full of features.
In fact I find it strange that it has all those other options like regex, text encoding, etc and not a well-working multiline search and replace.

---

### Post by ofb on 2007-08-27
> **KIAaze said:**
> Other than that it seems quite full of features.
In fact I find it strange that it has all those other options like regex, text encoding, etc and not a well-working multiline search and replace.

That's essentially my problem - I keep looking at these apps and thinking it *has* to be here somehow.

KFileReplace is quite the piece of kit, but it's like using a machine shop as a tin opener.

---

### Post by Jamie Jackson on 2008-01-18
regexxer seems almost perfect (very single-purpose), but it just doesn't have the tall text areas. So close! What gives, is there some insurmountable Linux hurdle preventing this?

See the multi-line enhancement requests: :(
[http://sourceforge.net/tracker/?group_id=64876&atid=508983]("http://sourceforge.net/tracker/?group_id=64876&atid=508983")

That websuite Java app is too much of a pain to use easily (unintuitive interface and configuration).

---

### Post by ofb on 2008-01-20
It gets worse.

Quanta, using KFileReplace, sandbags badly when processing an extensive extended S&R. Bluefish, using its built-in Replace, accomplishes the same task in about half the time, although it too can lock-up under heavy lifting.

The other detail is when using KfileReplace you cannot copy from the document panel(s) underneath to paste your choice of Search or Replace into KfileReplace. You need another editor open to copy items from. (Remember that you have to copy from somewhere for a multiline entry, because if you try typing it in, hitting Return for the new line is interpreted as Enter by KfileReplace and Bluefish's Replace.)

With Bluefish you can copy from the document panel - you're not locked out when the Replace panel is open.

I'll add that neither one automatically pastes highlighted choice into the search form when opened. You have always have two copy&pastes operations to perform. In all, it's remarkable backward compared to the decade-old Homesite. Most surprising.

So, yeah -- just mentioning that for anyone trying to use these editors. And if anyone is putting in the code effort to create tall-text entry forms, maybe you should work on Bluefish since it's a little more competent in this area.

---

### Post by Jamie Jackson on 2008-01-23
Thanks for posting your findings.

I came from Homesite+ on Windows, and now work in Linux. I get really frustrated every time I need this functionality (and I need it again today). Even the behemoth that is DreamWeaver has it.

I can't help but wondering which of the following is true:

[LIST=1]
[*]Linux folks don't know what they're missing, because they've never used an editor that has this functionality (otherwise, they'd have implemented it years ago)
[*]There *is* something available that we're missing 
[*]There's some dark force on the Linux platform that hinders the development of such tools.
[/LIST]

:confused:

---

### Post by ofb on 2008-01-30
How about, 4. Bad Luck ?

I don't know... as hugely popular as Homesite is/was with those who know it, that's not a lot of software users. Commerical outfits are tied to Dreamweaver, and the rest use readymade solutions like WordPress today. Extensive hand-coding is only done by a tiny minority that is further split in half because Mac owners use BBEdit.

And I'd guess Linux developers use regular expressions within Vi and Emacs, so they're no idea what the fuss is about.

So yeah, what's obvious to us just isn't to the greater world. Frustrating, yes. Bluefish is a clear copy of Homesite, but right after being delighted that it has Projects, you see it doesn't do S&R within Projects. It's kind-of a movie prop house - looks like it has a bathroom, but the plumbing isn't connected.

And re #2, sorry but no. I've really looked into this now. There isn't something we're missing. You've got two choices: Learn regular expressions or die on Linux, or try organizing a number of former Homesite users to help guide Bluefish and Quanta development to completion.

---

### Post by US41 on 2008-02-25
[http://techtrailerpark.blogspot.com/2008/02/banish-damn-command-line.html](http://techtrailerpark.blogspot.com/2008/02/banish-damn-command-line.html)

---

### Post by KIAaze on 2008-02-25
> **US41 said:**
> [http://techtrailerpark.blogspot.com/2008/02/banish-damn-command-line.html](http://techtrailerpark.blogspot.com/2008/02/banish-damn-command-line.html)

A point and click interface is what is being aimed for. Unfortunately, one that does exactly what is asked for here doesn't exist yet.
There doesn't even seem to be an easy command-line way to do it yet.

So sorry, if you didn't find a point-and-click solution here.
The closest that currently exists are the ones mentioned in this thread:
-Quanta
-KFileReplace
-Bluefish

cf 4 posts earlier:
> 
Quanta, using KFileReplace, sandbags badly when processing an extensive extended S&R. Bluefish, using its built-in Replace, accomplishes the same task in about half the time, although it too can lock-up under heavy lifting.

The other detail is when using KfileReplace you cannot copy from the document panel(s) underneath to paste your choice of Search or Replace into KfileReplace. You need another editor open to copy items from. (Remember that you have to copy from somewhere for a multiline entry, because if you try typing it in, hitting Return for the new line is interpreted as Enter by KfileReplace and Bluefish's Replace.)

With Bluefish you can copy from the document panel - you're not locked out when the Replace panel is open.

I'll add that neither one automatically pastes highlighted choice into the search form when opened. You have always have two copy&pastes operations to perform. In all, it's remarkable backward compared to the decade-old Homesite. Most surprising.

So, yeah -- just mentioning that for anyone trying to use these editors. And if anyone is putting in the code effort to create tall-text entry forms, maybe you should work on Bluefish since it's a little more competent in this area.

---

### Post by michaelzap on 2008-03-12
I also really miss this in Linux! I used to use Rapid PHP in Windows and it had this feature. This was actually one of the things that made me wonder whether I should completely switch to Linux or not (I did).

---

### Post by KIAaze on 2008-03-14
KFileReplace really seems to be the best. It offers two text boxes where you can enter multiple-line text if you click on the "+" button ("add string").

In Quanta, when you launch it using "plugins->KFileReplace", just click "search later".
This will launch KFileReplace embedded into Quanta. Then you'll have access to the "+" button. ;)

I tested it and it seems to work well as long as I don't use any regular expressions in there.
With regular expressions, it seems to replace all found text with only one replacement text instead of one for each match. :(
Maybe I'm just not good enough with regexs yet...

---

