---
title: "The basics...questions"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by aphex123 on 2007-07-22
Ok...Ive been searching all over google and can´t seem to find answers to a few basic things.


I have installed several programs using the Add/Remove Applications, easy.  example of the latest problem I had...should explain my frustraion.

apt-get install bzflag 
installs perfect from what I see....but where did it go?? I found an executable in the games folder but I dont think that is the actual install directory. It just seems to be an executable, no supporting files with it. Yes it runs there...but I baffled at where it goes. IF I want to run the server for example, where is the bzfs.conf file? The current guides on installing bzflag expect you to know where it went, how to get there:confused:

Most guides I find on installing do not explain the instalation process in general it mearly shows an example of how to do it using the commands for that specific program without explaining what each command actually does. I a little frustrated that it seems I must depend on finding someone else that has installed the same program and hope they show the correct commands. 

I like a little freedom to actually figure this out...Please point me to an up to date guide!

Thanks in advance,

bout to get linux for dummies but afraid it is out of date

---

### Post by Malibu Illusion on 2007-07-22
5 second Google search:

[http://www.faqs.org/docs/gazette/paths.html](http://www.faqs.org/docs/gazette/paths.html)

Google is your friend.

---

### Post by aphex123 on 2007-07-22
> **Malibu Illusion said:**
> 5 second Google search:

[http://www.faqs.org/docs/gazette/paths.html](http://www.faqs.org/docs/gazette/paths.html)

Google is your friend.

Thanks for the quick reply but that is exactly what Im talking about.

I&#314;l use just a small excerpt from that page. 

> Many software maintainers assert that they install in /usr/local/packagename not out of any method or philosophy, but rather because "we've always done it that way". And in the world of well-tuned software, if it isn't broke, it isn't fixed 

So...I look in  /usr/local/, no bzflag. 

I dont want to know the history of installing and where ppl think things should be installed. As I am still a windows user that comparison is like asking why I dont install in My Documents instead of Program Files...At this point I could care less at where it installs. I just want to know WHERE it installed. It was a perfect example of how most guides read, horrible for an absolute newb.

---

### Post by davidjmayo on 2007-07-22
Hi I see your frustration

look in /usr/bin/a_directory__similartoappname and you should find it

from a  terminal (applications==>accessories==>terminal) type

```
whereis bzflag
```

you can also do this for any app with whereis "appname"  change appname to what you want with no quotes

If you want to know where everything is use locate "appname" but you will get a big list !!

---

### Post by stmiller on 2007-07-22
davidjmayo: /usr/bin is not where programs are. /usr/bin is the location of executables.

The actual program is installed in /usr/share/bzflag

and config files are in

/home/yourname/.bzf

so just type

cd .bzf

to get to that directory.


BTW The search command you can use is locate.

$ locate bzflag

To update the search index type

$ sudo updatedb

---

### Post by davidjmayo on 2007-07-22
> **aphex123 said:**
> Thanks for the quick reply but that is exactly what Im talking about.

I&#314;l use just a small excerpt from that page. 



So...I look in  /usr/local/, no bzflag. 

I dont want to know the history of installing and where ppl think things should be installed. As I am still a windows user that comparison is like asking why I dont install in My Documents instead of Program Files...At this point I could care less at where it installs. **I just want to know WHERE it installed**. It was a perfect example of how most guides read, horrible for an absolute newb.


@stmiller sorry if I read this wrong but I thought OP was looking for the executable and you obviously know the package which I don't as you refer to /home/yourname/bzf
Note in my post I did also mention the locate command but maybe it wasn't clear

---

### Post by m3lt on 2007-07-22
The last several posts have helped a great deal!! Thank you!!

So how does the seasoned linux user know where things are installed? Must you run a locate cmd each time, or am I just overlooking something?

What is some good reading material to get started on this? Nothing I have found gives the step by step instruction. 

I hope you see where my frustration comes from...

Now since I just killed gnome while "installing" nvidia drivers I have to get gnome up so I can see what I'm doing.:lolflag:

The best thing about ubuntu/linux so far is the time it takes to do things. Seriously...I was bored of just point and click where this makes you actually work for things. Ya get a good sense of accomplishment when it works.

***Thanks again***...If I am still having problems when I sort out gnome Ill ask.

btw can the old list cmd work? from dos I mean...so if I dont have gnome up I can go to a dir and list the files in the dir.

---

### Post by davidjmayo on 2007-07-22
> **m3lt said:**
> The last several posts have helped a great deal!! Thank you!!

So how does the seasoned linux user know where things are installed? Must you run a locate cmd each time, or am I just overlooking something?
[COLOR="Blue"]use the commands you saw already: "whereis" or "locate" or just type the app name which is usually the same but sometimes it maybe a little different. this link has an overview of the file system and you can look at the other pages [http://linuxcommand.org/lts0040.php](http://linuxcommand.org/lts0040.php) [/COLOR]
What is some good reading material to get started on this? Nothing I have found gives the step by step instruction. 
[COLOR="Blue"]This link has a lot of free books you can download. don't thank me, thank the poster of the thread as I didn't find it [http://ubuntuforums.org/showthread.php?t=484846](http://ubuntuforums.org/showthread.php?t=484846)[/COLOR]
I hope you see where my frustration comes from..

Now since I just killed gnome while "installing" nvidia drivers I have to get gnome up so I can see what I'm doing.:lolflag:
[COLOR="Blue"]I don't have nvidia[/COLOR]
The best thing about ubuntu/linux so far is the time it takes to do things. Seriously...I was bored of just point and click where this makes you actually work for things. Ya get a good sense of accomplishment when it works.

***Thanks again***...If I am still having problems when I sort out gnome Ill ask.
[COLOR="Blue"]sorry I use Kubuntu and can't remember the Gnome command[/COLOR]
btw can the old list cmd work? from dos I mean...so if I dont have gnome up I can go to a dir and list the files in the dir. see link number 1from the beginning


[COLOR="Blue"]HTH David[/COLOR]

---

### Post by steve.horsley on 2007-07-22
If you install a package with Synaptic, you can then right-click the package (in Synaptic), select Properties and see a file list fo all the files it installed. Very handy. I'm sure man apt-get will reveal a text mode way to do the same thing of you prefer.

---

