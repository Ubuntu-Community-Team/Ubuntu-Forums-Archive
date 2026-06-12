---
title: "awn installation"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by limac on 2007-10-20
I was trying to install awn on my gutsy final release. I tried and followed the instructions on [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981) and after placing the final command on the terminal it says: 

ron@limac:~$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avant-window-navigator-bzr

I don't know what to do to get awn on my gutsy. Actually I have a intel graphics card not an nvidia one. So does the problem have anything to do with that?

Thnx

---

### Post by Paqman on 2007-10-20
> **limac said:**
> Actually I have a intel graphics card not an nvidia one. So does the problem have anything to do with that?


Nope, the problem is that apt-get can't find the right package to download. Can you confirm that you have those repos enabled? (are they in System > Administration > Software Sources > 3rd Party?)

---

### Post by Pumalite on 2007-10-20
[http://ubuntuforums.org/showthread.php?t=583007](http://ubuntuforums.org/showthread.php?t=583007)

---

### Post by limac on 2007-10-20
Huh?

---

### Post by limac on 2007-10-20
what do you mean by that? enable the options in 3rd party software?

---

### Post by Paqman on 2007-10-20
In the first step of that guide you added two new repos:
```

deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator

```

The guide asked you to manually add them to etc/apt/sources.list. By going to Software Sources you can see all the repos in that list. Are those repos listed?

---

### Post by limac on 2007-10-20
I added those repos in the first step to the sources-list. and what do I do after adding those repos in the sources-list?

---

### Post by Paqman on 2007-10-20
> **limac said:**
> and what do I do after adding those repos in the sources-list?

You paste the series of commands:

```

wget http://download.tuxfamily.org/syzygy42/reacocard.asc
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update

```

into a terminal window. After the apt-get update one it'll scroll through loads of text as it updates itself. After that you should be able to download the awn packages

---

### Post by JBAlaska on 2007-10-20
After you add the above repo's, go to synaptic package manager and serch for 
```
avent window navigator
```

add avant and the awn plugins and your done.

---

### Post by limac on 2007-10-20
After placing that command in the terminal this is what it says:

ron@limac:~$ wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
--10:44:25--  [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
           => `reacocard.asc'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,682 (1.6K) [application/octet-stream]

100%[====================================>] 1,682         --.--K/s             

10:44:26 (154.13 MB/s) - `reacocard.asc' saved [1682/1682]

ron@limac:~$ sudo apt-key add reacocard.asc
[sudo] password for ron:
OK

That's all it says.So what will be the next thing I have to do?

---

### Post by limac on 2007-10-20
no results are shown in the synaptic manager after i put "avent window navigator" in it.

---

### Post by Paqman on 2007-10-20
> **limac said:**
> After placing that command in the terminal this is what it says:

ron@limac:~$ wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
--10:44:25--  [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
           => `reacocard.asc'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,682 (1.6K) [application/octet-stream]

100%[====================================>] 1,682         --.--K/s             

10:44:26 (154.13 MB/s) - `reacocard.asc' saved [1682/1682]

ron@limac:~$ sudo apt-key add reacocard.asc
[sudo] password for ron:
OK

That's all it says.So what will be the next thing I have to do?

Looks like you only pasted in the first two lines. Try the third and then fourth ones.

---

### Post by limac on 2007-10-21
what do I do after simply adding those lines in the /ect/apt/sources.list?

And even after adding those four lines it can't find avent window navigator.

---

### Post by Pumalite on 2007-10-21
It's 'avant '

---

### Post by limac on 2007-10-21
i trie it w/that but didn't work either

---

### Post by tenmillionmilesaway on 2007-10-21
now do this:

```
sudo apt-get update
```

when that has finished do this:

```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
```

by do i mean paste into a terminal and press enter

---

### Post by limac on 2007-10-21
this is what it says:

"ron@limac:~$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avant-window-navigator-bzr"

And that's the problem i've been facing

---

### Post by limac on 2007-10-21
hey,
this is what it says:

"ron@limac:~$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avant-window-navigator-bzr"

And that's the problem i've been facing

---

### Post by limac on 2007-10-21
so that is the problem i am facing

---

### Post by oilchangeguy on 2007-10-21
is there a special reason why you started another thread on the same subject?
[http://ubuntuforums.org/showthread.php?t=585555](http://ubuntuforums.org/showthread.php?t=585555)

---

### Post by limac on 2007-10-21
srry about that. I didn't really notice

---

### Post by tenmillionmilesaway on 2007-10-21
did you do the sudo apt-get update first.  if so then you havent added the repos correctly.  this is what you should have done:

```
gksu gedit /etc/sources.list
```

pasted the two lines into the file

closed and saved the file.

You have already added the key for the repo so after added you should be ready to go

---

### Post by limac on 2007-10-21
one tiny thing. how exactly do u use the /etc/apt/sources-list. i mean after simply copying and pasting the two lines into the file. What do u do then? 

Please explain

---

### Post by Pumalite on 2007-10-21
You can go to Synaptic>Reload>Search>avant-window-navigator>Install all three

---

### Post by tenmillionmilesaway on 2007-10-21
> **limac said:**
> one tiny thing. how exactly do u use the /etc/apt/sources-list. i mean after simply copying and pasting the two lines into the file. What do u do then? 

Please explain

just save the file then

```
sudo apt-get update
```

to make it check the new repos

---

### Post by limac on 2007-10-21
well yeah, but what i was talking of was what do u do after just copying and pasting the codes into /etc/apt/sources-list. Like clik on save or what?

---

### Post by mlentink on 2007-10-21
yes.
Click on save.
Close the editor.
Got to System>Administration>Synaptic Pacjage Manager
Enter your Password as asked for
Click on Update System
Search for avant-window-navigator
tick the check boxes befotre the applicable packages
hit Apply
wait till it is installed...

---

### Post by limac on 2007-10-21
> **tenmillionmilesaway said:**
> just save the file then

```
sudo apt-get update
```

to make it check the new repos

so after adding the lines in the file I basically save it choosing a name, and then i put that command in the terminal, then enter?

Am i on the right track?

---

### Post by mlentink on 2007-10-21
> **limac said:**
> so after adding the lines in the file I basically save it choosing a name, and then i put that command in the terminal, then enter?

Am i on the right track?

No.
You do not have to choose a name. The file already has a name, so just save it.Then proceed as suggested above.

---

### Post by limac on 2007-10-21
where is 'update system" on synaptic package manager?

---

### Post by mlentink on 2007-10-21
Synaptic will show you first a row of menu commands (probably starting with, in english " file" ), then below it at row with icons (which equally represent commands, starting with " Reload" ). Click the second from the left in the second row.

---

### Post by limac on 2007-10-21
but that one says "Mark All Upgrades"

---

### Post by avik on 2007-10-21
> /etc/apt/sources-list

It's /etc/apt/sources**.**list

It should already have a number of entries in it.

---

### Post by limac on 2007-10-21
yeah, i originally entered that but I guess I just typed that /etc/apt/sources-list accidentally.

What do u mean by "It should already have a number of entries in it"

Thnx

---

### Post by mlentink on 2007-10-21
> **limac said:**
> but that one says "Mark All Upgrades"

What does the on immediatley to the right say

Oops. Getting late... to the left, I mean. Should be something like ' Reload' in english....
If you hit that, it'll refresh your sources. Then you cn search for the package, mark it and apply

---

### Post by mlentink on 2007-10-21
> **limac said:**
> What do u mean by "It should already have a number of entries in it"
What he means is that there should already be quite a few sources for software listed in that file.

---

### Post by limac on 2007-10-21
what do U mean by "What does the on immediatley to the right say"

---

### Post by JBAlaska on 2007-10-21
Click to enlarge:
[[IMG]http://img81.imageshack.us/img81/9012/avantsearchsw2.th.png[/IMG]](http://img81.imageshack.us/my.php?image=avantsearchsw2.png)

---

### Post by limac on 2007-10-21
thanks for the info jbalaska

---

### Post by limac on 2007-10-21
and another thing**_ where_** do I save the /etc.apt/sources.list? The default location which is folder 'etc' or somewhere else?

---

### Post by JBAlaska on 2007-10-21
After you do;
```
gksu gedit /etc/apt/sources.list
```

And add the repo lines, you can just close gedit and click save when asked.

that will save sources.list which is at **/etc/apt/sources.list**

---

### Post by limac on 2007-10-21
after installation what should I do to enable avant windows navigator?

---

### Post by limac on 2007-10-21
and if I click on my awn manager, it's not responding, in other words it not opening when I click on it. Why is that?

---

### Post by Pumalite on 2007-10-21
You need compiz-fusion installed or Beryl

---

### Post by limac on 2007-10-22
thanks for all the help.now i'm successful in running awn because of all your help. so thanks again.

---

### Post by quantumX3 on 2007-10-22
Like limac, when I click the Awn manager, it doesn't respond.  The funny thing is I DO have compiz-fusion installed as I'm running gutsy and using the cube effect while I type this! : )
Any ideas why it won't respond/open?

---

### Post by avik on 2007-10-23
Can you post the output of avant-window-navigator in the terminal?

---

### Post by quantumX3 on 2007-10-23
Hey sorry, I figured out that AWN needs to be run like an application!  After you said to fire it up in the terminal I did that and behold it works now!  I thought that I configured AND enabled it throught the manager like compiz.  Is there a why to ensure that AWN will start automatically upon start up?

Thanks for your guys help...it's great to be able to have a better,more powerful and free alternative to Vista!

---

