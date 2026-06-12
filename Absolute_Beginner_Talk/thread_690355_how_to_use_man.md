---
title: "how to use man"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by HugoRune on 2008-02-07
Somae basic and probably stupid questions about man:

1) how do I use man? 
Trought trial and error I found out that "q" exits.  Where can I find the other controls, and why are they not found under "man man"?

2) how do I follow references in man?
For example "man debconf" says in the first paragraph "see _debconf_(7)". It looks like a link, but no key could coax man to follow it. After carefull study of "man man"  I concluded that just maybe 7 refers to a "section", which I could add as a parameter to the command line. But neither "man 7 debconf" nor "man debconf 7" nor "man debconf(7)" brought me any closer.

3) How do I find the answers to questions like these without consulting a forum? There must be an easier way? How did you manage to do this?

---

### Post by emarkd on 2008-02-07
man [section] [title] is the format, so man 7 debconf will work if the documentation is there.  [Here's]("http://www.linuxdevcenter.com/linux/cmd/") a great online resource for learning about Linux commands.

---

### Post by hyper_ch on 2008-02-07
dunno actually... when I want to search / copy'n'paste I do this:

```

man XYZ > ~/Desktop/XYZ.txt

```

---

### Post by erfahren on 2008-02-07
you can look at the man pages here as well (somewhere on the site there's a way to download the whole thing) - comes in handy
[http://www.linuxcommand.org/superman_pages.php](http://www.linuxcommand.org/superman_pages.php)

---

### Post by monte48lowes on 2008-02-07
I believe 'man' uses the functions of 'less' to display the man pages. So for information on how to navigate man pages use:

```
man less
```

Additionally, konqueror can display man pages by typing 'man:' in the address bar. I don't know if that is available in nautilus or not.

Mike

---

### Post by Cypher on 2008-02-07
Ironically enough..
```

man man

```
;)

---

### Post by hyperair on 2008-02-07
When man'ing something, press 'h'. Then the help screen will appear. =)

---

### Post by HugoRune on 2008-02-07
> **monte48lowes said:**
> I believe 'man' uses the functions of 'less' to display the man pages. 

Thanks! That seems to be the list of commmands used in man. Well hidden indeed.


[QUOTE=Cypher]Ironically enough.. man man
[/QUOTE]
not sure what you are trying to say? Are you certain you read my question?


emarkd, erfahren: both links seem useful, but I cannot find any entry about debconf in either?


[QUOTE=hyperair]
When man'ing something, press 'h'. Then the help screen will appear. =)
[/QUOTE]
Thanks! I do not know how I missed that. I thought I tried every key.

---

### Post by Cypher on 2008-02-07
The text with underlines that appear to be links in man pages are not indeed links, the underline is used just to highlight the text.

It is also possible that some man pages might refer to other pages that don't actually exist, so in the case of debconf, it says to see debconf(7) which doesn't exist..

You can see all the man pages that on your system by looking at the /usr/share/man/man* directories..so there should be a debconf.7.gz file in /usr/share/man/man7 and you'll probably find that it doesn't exist. However, if you were to do "man 7 icmp" it will work as icmp does exist in that directory..

---

### Post by Whiffle on 2008-02-07
If you're lazy like me, open up konqueror and type 

man:/

into the address bar.  Or man:/nameofprogram.

---

### Post by MarkX on 2008-02-07
It depends what country you are in and what people you talk to.
For example, if you ask a bank manager here in england: "yeo MAN, I need some dough for me biatch" you might not be as sucessful as saying "Good afternoon, I would like  to take out a loan."
OTOH if you were listening to some 60's music in appropriate company and you said: "Wow MAN, cool vibes" you'd gain more street cred than pronouncing: "I say! That is a jolly spiffing tune, old Bean!".

---

