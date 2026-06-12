---
title: "Downgrading?????"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by Mediciman on 2006-11-13
I was wondering If I could downgrade from 6.10 Ubuntu to 6.06 Because I would be able to get help to get my Wireless working on that and nobody knows how on 6.10. I was wondering If I could do this without a live cd?????????????:confused: :confused:

---

### Post by an.echte.trilingue on 2006-11-13
simply edit /etc/apt/sources.list and change every instance of edgy to dapper and then 
```

sudo apt-get update
sudo apt-get upgrade
```

There is no garantee it will be problem free but it is better than re-installing.

---

### Post by Mediciman on 2006-11-13
Im really really sorry But I'm really slow when it comes to this Can you Explain that gain?
The first part.

---

### Post by goldenatom on 2006-11-13
Open up /etc/apt/sources.list using 

```
sudo gedit /etc/apt/sources.list
```

Then every place that you see "Edgy" change it to "Dapper"

---

### Post by Henry Rayker on 2006-11-13
I believe what s/he wants you to do is open

/etc/apt/sources.list for editing

```
sudo gedit /etc/apt/sources.list
```

and change every instance of the word "edgy" to "dapper"

EDIT: beaten to it.

---

### Post by Mediciman on 2006-11-13
Ok thank you so much.
I might get stuck so...Be there to help me. heh. anyway thanks.

---

### Post by an.echte.trilingue on 2006-11-13
Just because I cannot explain things well does not mean that you are slow.

Anyway, downgrading a distro is essentially the same thing as upgrading it.  You need to tell the package manager (aka, program manager) where to look for its packages, and then to install those packages.

So, the first step is to edit the file that our package manager, apt, uses to know where to look for those packages.  This file is located in the folder /etc/apt/ and it is called sources.list.  So, to edit it, you need to open a text editor and since only root (the system admin account) can edit this file, you need to have root access to do this.  So, the command is:

```
sudo gedit /etc/apt/sources.list
```

of course, if you are using kubunty you replace gedit with kate, or whatever your prefered text editor is.

Now, luckily for us Ubuntu keeps all of the programs for all of its distros in the same place, so you only need to change one word in each line to reflect the change you want to make.  Basically, you look for each instance of the word "edgy" and replace it with "dapper".  You save and close.

Now, apt does not know about this change yet, so you need to run an update:

```
sudo apt-get update
```

apt will download the list of all the programs available for dapper, basically the whole distro.

Then we need to upgrade and replace all the programs installed locally with the ones in the repositories and redo all the config files:

```
sudo apt-get dist-upgrade
```

This will take a long time and apt will have to download lots of stuff, but when it is done you should be able to reboot into a brand new dapper machine.

A warning, though, is that this could break your system, especially if you did a lot of your config files by hand.  Be prepared to re-install.

Good Luck!
-mat

---

### Post by David Corrales on 2006-11-13
The problem is, by default apt will prefer newer versions of packages. If I were you, I'd do a clean install.

---

### Post by Mediciman on 2006-11-13
But when I try and Edit it it says I can't and when I put in the code it wants a password witch I can't put in.

---

### Post by goldenatom on 2006-11-13
Its the password that you use to log on to Ubuntu. Give that a try.

---

### Post by Mediciman on 2006-11-13
No I mean it won't let me type it in.

---

### Post by goldenatom on 2006-11-13
The "sudo" in the code is what gives you the privileges to edit your sources list, thats why you just can't open it and edit it.

---

### Post by goldenatom on 2006-11-13
It won't let you type it in? Hmm. Oh, well, it won't look like you're typing anything in. Just type it in and hit enter.

---

### Post by taurus on 2006-11-13
Please, try to use gksudo when you use it with gedit!!!

```
gksudo gedit /etc/apt/sources.list
```

p.s.  When you type in your password, you won't see it echo back so don't worry about it...

---

### Post by Mediciman on 2006-11-13
Ok I will Try.

---

### Post by Mediciman on 2006-11-13
Ok I just did that taurus Now it opened now what do I do???

---

### Post by taurus on 2006-11-13
Use the arrows to move around and replace edgy back to dapper.  Save it and run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Mediciman on 2006-11-13
Ok I Put that code in then it opened up A black Window Titled sources.list. So what Do I do With it?

---

### Post by Mediciman on 2006-11-13
Blank Window After I put in the gksudo one.

---

### Post by taurus on 2006-11-13
> **Mediciman said:**
> Blank Window After I put in the gksudo one.
Not sure what you mean here?  You put in gksudo of ...  Can you include the exact command that you use?

---

### Post by Mediciman on 2006-11-13
I put this in.
gksudo gedit /etc/apt/sources.list in the terminal.
Then it ask for my password I put it in.
Then it opened Up Sources.list.

---

### Post by taurus on 2006-11-13
Now use your arrow keys to navigate around and replace the word edgy with dapper and save the changes...

---

### Post by Mediciman on 2006-11-13
Well there isn't any thing on the page. :(

---

### Post by bulldog on 2006-11-13
> **Mediciman said:**
> Well there isn't any thing on the page. :(

Are you logged in with the live cd?

---

### Post by Mediciman on 2006-11-13
Nope. I'm not.

---

### Post by taurus on 2006-11-13
So you see anything when you enter this command from a terminal?

```
cat /etc/apt/sources.list
```
p.s.  Better extra careful with lower letters with upper letters because Linux/Unix is case sensitive!!!

---

### Post by Mediciman on 2006-11-13
It says no Such file.

---

### Post by taurus on 2006-11-13
Okay, what about the output of this command then?

```
ls -la /etc/apt
```

---

### Post by bulldog on 2006-11-13
Are you absolutely sure nobody can help you with your wireless trouble?
Did you post it at the right thread?
Did you take a look inhere? 

[http://ubuntuforums.org/search.php?searchid=9759577](http://ubuntuforums.org/search.php?searchid=9759577)

A blank sources.list isn't gonna help,and if you have no internet on the computer,it could be a little tricky I guess.

But I let Taurus to it,he's much more experienced than I am.

---

### Post by Mediciman on 2006-11-13
It says Command Not found.

---

### Post by taurus on 2006-11-13
> **Mediciman said:**
> It says Command Not found.
Are you SURE you type exactly like that in a terminal?  

```
ls -la /etc/apt
```

---

### Post by Mediciman on 2006-11-13
So thats a Capital I and a space Between Is and -la and -la and /?
Just making sure

---

### Post by taurus on 2006-11-13
It's a lower case letter l as in larry!!!  Instead of typing, you should use the cut 'n paste...  Left mouse to cut and middle mouse (or both left and right at the same time) to paste...

---

### Post by Mediciman on 2006-11-13
Oops Sorry I'm kinda Tired.

---

### Post by Mediciman on 2006-11-13
It says no such File found.

---

### Post by dannyboy79 on 2006-11-13
> **Mediciman said:**
> I put this in.
gksudo gedit /etc/apt/sources.list in the terminal.
Then it ask for my password I put it in.
Then it opened Up Sources.list.

I think this might be the key here, he says, "Then it opened Up Sources.list." Notice the captial S in Sources.list, that might be the problem, gedit created a new file and that's why it's empty. This guy doesn't know that Linux is case sensitive. It also sounds like he needs to read some basics on Ubuntu or even linux. I would send him over to the Wiki or have him read some Linux start webpages. It's kind of hard to help some1 when they ask you want they are suppose to do 8 times, and you have told them how to do it each of those times. Don't get me wrong, I am all about making the Ubuntu Community grow but it would be very wise to read up about an OS before you just install it and don't even know how to edit a file. Am I wrong here?

---

### Post by dannyboy79 on 2006-11-13
tell us what happens when you CUT AND PASTE this into your terminal session

sudo find / -name source*

---

### Post by Mediciman on 2006-11-13
No..I just have a problem with making letter upper case.
it is "sources.list"
And I did read up on it.

---

### Post by Mediciman on 2006-11-13
Uh ok I will try.

---

### Post by Mediciman on 2006-11-13
Well I did that then it Came up with a bunch of stuff in the terminal.

---

### Post by dannyboy79 on 2006-11-13
That other way with find might not work, it's weird. Try to copy and paste this into the terminal

ls /etc/apt

and copy and paste exactly what it spits out.

---

### Post by dannyboy79 on 2006-11-13
> **Mediciman said:**
> Well I did that then it Came up with a bunch of stuff in the terminal.

It doesn't help us help you by saying that????? Please post the output. THANX

---

### Post by goldenatom on 2006-11-13
what does gksudo do exactly?

---

### Post by taurus on 2006-11-13
> **goldenatom said:**
> what does gksudo do exactly?

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Mediciman on 2006-11-13
Ok I will Do that. And I will try that one.

And it opens up "sources.list"
It is a blank Page.

---

### Post by dannyboy79 on 2006-11-13
> **goldenatom said:**
> what does gksudo do exactly?

please don't take this thread off topic, you can find out about it using gogle or the search function within this forum. Here I did it for ya in a second, [http://www.ubuntuforums.org/archive/index.php/t-165957.html](http://www.ubuntuforums.org/archive/index.php/t-165957.html).

---

### Post by Mediciman on 2006-11-13
Ok The ls /ect/apt Says No such file.
and The other one says

/ect/apt/sources.list.d
/ect/apt/sources.list
/ect/apt/Openoffice
/ect/apt/Gnome 
/ect/apt/Gnome
/ect/apt/doc
/ect/apt/doc
/ect/apt/doc
/ect/apt/linux-headers
/ect/apt/linux-headers

That it.

---

### Post by dannyboy79 on 2006-11-13
> **Mediciman said:**
> Ok I will Do that. And I will try that one.

And it opens up "sources.list"
It is a blank Page.

Mediciman, you should use the quoted response once in awhile so we know who you are responding to?? I have asked you to paste the output of the find command and you haven't done that?? If you want our help, well I guess I should speak for myself, but if you want my help then you're going to have to help me help you, if I ask you for some output then let me see it, if you don't give it to me than why are you here asking for help if when I try to help you you don't want to listen??? I am really trying to be patient here as I am sure you a new user but you are making this very difficult to help you.

---

### Post by Mediciman on 2006-11-13
> **dannyboy79 said:**
> Mediciman, you should use the quoted response once in awhile so we know who you are responding to?? I have asked you to paste the output of the find command and you haven't done that?? If you want our help, well I guess I should speak for myself, but if you want my help then you're going to have to help me help you, if I ask you for some output then let me see it, if you don't give it to me than why are you here asking for help if when I try to help you you don't want to listen??? I am really trying to be patient here as I am sure you a new user but you are making this very difficult to help you.
Ok..Sorry then..

---

### Post by dannyboy79 on 2006-11-13
> **Mediciman said:**
> Ok The ls /ect/apt Says No such file.
and The other one says

/ect/apt/sources.list.d
/ect/apt/sources.list
/ect/apt/Openoffice
/ect/apt/Gnome 
/ect/apt/Gnome
/ect/apt/doc
/ect/apt/doc
/ect/apt/doc
/ect/apt/linux-headers
/ect/apt/linux-headers

That it.

Are you f__king with us???? oh my god, how did you rename your etc folder to ect?????? if this is true than the command you need to use is 

gksudo /ect/apt/sources.list


and it'll work, then just do what they all posted in the first page of this thread. you can open 2 windows of firefox or whatever browser at once to see what it says without losing this page.
then you need to figure out how you renamed your ect folder and how the world your computer is still functioning. doesn't the computer read from the etc folder everyone??? how can this be.

---

### Post by dannyboy79 on 2006-11-13
> **Mediciman said:**
> Ok..Sorry then..


you don't have to be sorry. I am really trying to help you, it's just kind of frustrating when I try to help but you don't help ME help you. You know what I mean?

---

### Post by Mediciman on 2006-11-13
> **dannyboy79 said:**
> Are you f__king with us???? oh my god, how did you rename your etc folder to ect?????? if this is true than the command you need to use is 

gksudo /ect/apt/sources.list


and it'll work, then just do what they all posted in the first page of this thread. you can open 2 windows of firefox or whatever browser at once to see what it says without losing this page.
then you need to figure out how you renamed your ect folder and how the world your computer is still functioning. doesn't the computer read from the etc folder everyone??? how can this be.
Yeah your going to get mad..I ment etc sorry.
I'm on a differnt Computer I wrote all of it down but typed it down wrong. sorry.

---

### Post by dannyboy79 on 2006-11-13
oh, so you can't copy and paste because you are on a differnet computer? why are you doing it this way?? anyway, so then if it is /etc/ then the command 

gksudo gedit /etc/apt/sources.list 

should work just fine. if the file is still empty than also do the same command with this

gksudo gedit /etc/apt/sources.list.d

and tell me if that file is also empty. if it is, then please tell me what kind of install this is and what the h_ll you have done to your sources.list file. :-)

---

