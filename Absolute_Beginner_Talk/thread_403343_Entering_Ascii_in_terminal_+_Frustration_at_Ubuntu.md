---
title: "Entering Ascii in terminal + Frustration at Ubuntu Resources"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by ing on 2007-04-06
Hi, as you can see this is my first post so "hey!" to the community....

First of all can someone please tell me how to enter ASCII characters, specifically characters outside of the alphabet / numbers in a Linux terminal. (I'm talking remote login through ssh, no GUI). As some joker has uploaded some files to my server with file names containing non-keyboard characters and I cannot enter the file names in order to do anything with them.

Also I'd like to comment on the regular frustration which I have faced since embarking on Ubuntu (Server) some weeks ago, every time I have hit a wall I have found it near impossible to find a clear concise answer to the most simple of questions (such as the one above). The net seems to be full of information on Linux, yet 90% of it seems to be completely useless information duplicated many times over in different sources. It is either incomplete, in concise or missing altogether. Coming from a windows environment which despite it's (many) downfalls, I have never found it hard to resolve issues via some light research. I really hope that this is not simply the nature of open source, because I really don't want the corps to win....

The Ubuntu guide and Ubuntu server guides seem completely useless (outside of initial setup) and I have gleaned zero knowledge from having read a large part of these, are there any important resources which I should know of which may help this poor Linux noobie for this or for future (expected) problems? I really would like to get to grips with administering Linux properly but as I said, I find myself spending large amounts of time dealing with minor issues and getting rather frustrated.

Apologies if the question (before my rant) is covered here or somewhere equally as obvious.
Have pity on the lost geek..... :(

---

### Post by devnulljp on 2007-04-06
If all you need to do is remove those files, you can use a regex with a readable part of the filename and do it that way, or select the filename and dump it into your command line with a middle click (I know you said no GUI--although you can forward X over ssh with ssh -X, so there's no real reason why you can't have a gui if you want one--but if you're using a terminal from X you should be able to use the mouse to highlight and past things aroung your terminal session)
 
Why not document the problems you're having, with solutions when you find them and put that up for others to read later too?

---

### Post by ing on 2007-04-07
Thanks for the reply.

I am now connecting through ssh with X forwarding (<3 Putty), and after looking up how to copy and paste in the terminal (highlight to copy and right click to paste for any other nabbs), I have been able to fix the problem of using extra characters. Thanks.

I will be using these forums as my primary resource in the future, and will try and contribute any solutions I find which may be handy for those (few) who are still a step behind me in the Ubuntu environment. Anyway, back to work....

---

### Post by freebird54 on 2007-04-07
In case you hadn't found it yet, the keyboard equivalents are related to DOS ones too.  <shift><end> to highlight (or <shift><arrow> ).  <ctrl><shift> with X=cut C=copy and V=Paste.  Once picked up in terminal, <ctrl> with those keys will work in almost all graphic apps - you only shift within the terminal (as ctrl sequences were already "taken".

Hope it helps.  Still haven't found a similar method like <alt> + numpad numbers to enter chars though.  Seems a strange oversight!

---

### Post by ing on 2007-04-07
Aye, I thought so to. Assumed that there would indeed be a <ALT>+nums style input and was surprised to find there wasn't.

Thanks for the input.

---

### Post by briandotcom0 on 2008-01-10
ctrl+Shift+u or just Ctrl+shift depending on your version will allow you to type unicode characters, but I want ascii, so if you can find out how to do ascii, please post.

---

