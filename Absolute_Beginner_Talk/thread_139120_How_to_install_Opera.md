---
title: "How to install Opera?"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by Zdravko on 2006-03-03
I noticed I have already installed Firefox 1.07 on Ubuntu 5.10, but I really would like to use Opera. How can I remove this Firefox and then install Opera?

---

### Post by dwessell on 2006-03-03
If you go into the How To Forums, there's an installer called Automatix.. It will install Opera automatically for you, as well as a bunch of other items.. I've used it on a computer in the network, and it's been pretty useful.. Easy too..


dw

---

### Post by anacron on 2006-03-03
use search next time, before posting "stupid questions" will ya? :)
there's plenty of "howto install opera" tutorials, automatix can do that too.

there's no reason to remove firefox, except if you want free space...
anyway, you can remove firefox with:
```
sudo apt-get remove mozilla-firefox 
```
or with synaptic etc...

---

### Post by Zdravko on 2006-03-03
Hmm, yeah, I know I am a newbie. But this is this forum for? Anyway I couldn't find Opera in any application list (synaptc or whatever). Do I need to go to opera's website and download it from there?

---

### Post by ajgreeny on 2006-03-03
Add this line to your sources.list (/etc/apt/sources.list) and you should find opera listed in synaptic after you have done an update of repositories.  I don't like opera so have not got it uncommented in my list so I don't know which version is there, but something should be.

---

### Post by Zdravko on 2006-03-03
ajgreeny, what line are you talking about?

---

### Post by Stereotypical Rage on 2006-03-03
Go to Opera.com and download the tar.gz file, extract it to a folder. Then navigate to that folder via a terminal, then run install.sh

---

### Post by Zdravko on 2006-03-03
Stereotypical Rage, it appears that the *.sh script is attempting to install Opera in my personal directory. Is this normal for Ubuntu/Linux at all? Or do I have to specify some other place?

> 
Files will be installed as follows:
-----------------------------------------------------------
 Wrapper Script : /home/zdravko/bin
 Binaries       : /home/zdravko/lib/opera/8.52-20060201.6
 Plugins        : /home/zdravko/lib/opera/plugins
 Shared files   : /home/zdravko/share/opera
 Documentation  : /home/zdravko/share/doc/opera
-----------------------------------------------------------
Is this correct [ y,n,c | yes,no,cancel ] ?


---

### Post by Stereotypical Rage on 2006-03-03
I honestly don't know. You might want to make the folder "Opera" in /opt/. I installed everything to the  home dir, I do believe. I too am new to Opera.

I'm testing Opera 9.0 PR2 right now.

---

### Post by Klaidas on 2006-03-03
How about installing Opera with Automatix? :)

---

### Post by Perfect Storm on 2006-03-03
Open your terminal (Application ---> Accessories ---> Terminal)

Write:
```
sudo gedit /etc/apt/sources.list

```

add:
[b]## Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
[/b]

then:
```
sudo apt-get update
sudo apt-get install opera
```

To start Opera, simply type opera in the terminal, remember that linux is case sensitive.

---

### Post by Stereotypical Rage on 2006-03-03
I couldn't do that since I'm on Dapper.:p

---

### Post by Perfect Storm on 2006-03-03
Ah...I see, can't help you there, still on breezy since I need a stable system.

---

### Post by Stereotypical Rage on 2006-03-03
[QUOTE=Artificial Intelligence]Open your terminal (Application ---> Accessories ---> Terminal)

Write:
```
sudo gedit /etc/apt/sources.list

```

add:
[b]## Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
[/b]

then:
```
sudo apt-get update
sudo apt-get install opera
```

To start Opera, simply type opera in the terminal, remember that linux is case sensitive.[/QUOTE]
The debs have unresolved dependancies. It's best to install via the tar.gz. I read that on here somewhere.

---

### Post by Perfect Storm on 2006-03-03
Are we talking for dapper or in general? Because I've no trouble at all with it or any dependcy problems.

---

### Post by cotcot on 2006-03-03
I used this with succes :  [https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)

---

### Post by Stereotypical Rage on 2006-03-03
[QUOTE=Artificial Intelligence]Ah...I see, can't help you there, still on breezy since I need a stable system.[/QUOTE]
To me Dapper is way more stable than Breezy was. Much much faster. ZOOM ZOOM!

 I've used every version of Ubuntu. Remembers the early days of Warty. :sniff: (Still a newbie though)

---

### Post by Zdravko on 2006-03-03
A.I., thank you, I will give it a try...

---

### Post by kadymae on 2006-03-03
Since I really don't like tar.gz files and the fact that you have to know which subspecies of tar.gz you're dealing with to install them at the command line, I head straight for the .deb file.

Go to the Opera site and it will guide you to a debian based download.  

Download.

Drag to your home folder

Open the terminal

at the $ prompt type  ls

You should see the contents of your home folder listed.

Then type sudo dpkg -i op  
(and hit the tab key to force the computer to type the rest of that gawdawful long file name)
Then hit the enter key

It should install.

to check that it has type opera after the prompt and it should launch.  You should also be able to open and run it from your applications menu.

---

### Post by Stereotypical Rage on 2006-03-03
[QUOTE=Artificial Intelligence]Are we talking for dapper or in general? Because I've no trouble at all with it or any dependcy problems.[/QUOTE]
I had the dependancy problem with Breezy. I didn't like it. So I waited till I got Dapper, and tried to install the deb and it failed. So I installed the TAR.GZ file and it works like a charm, aside from the Menu Icon not appearing.

---

### Post by Zdravko on 2006-03-03
I installed Opera. Very nice. Now I want to add some other language interface. But where to place that *.lng? I noticed that the eng.lng is located in the /usr/share/opera folder. I would like other language files for Opera to reside there.

---

### Post by jpkotta on 2006-03-03
[QUOTE=Stereotypical Rage]I had the dependancy problem with Breezy. I didn't like it. So I waited till I got Dapper, and tried to install the deb and it failed. So I installed the TAR.GZ file and it works like a charm, aside from the Menu Icon not appearing.[/QUOTE]

You can add it to the menu manually.  See the [wiki]("https://wiki.ubuntu.com/OperaBrowser#head-180d7c7b6dd969452592944e8dfd152d059c1708").

---

### Post by Perfect Storm on 2006-03-03
[QUOTE=Stereotypical Rage]I had the dependancy problem with Breezy. I didn't like it. So I waited till I got Dapper, and tried to install the deb and it failed. So I installed the TAR.GZ file and it works like a charm, aside from the Menu Icon not appearing.[/QUOTE]

Aye, that's great ^^...There are more than one way to skin thte cat :mrgreen:

---

### Post by Stereotypical Rage on 2006-03-03
[QUOTE=jpkotta]You can add it to the menu manually.  See the [wiki]("https://wiki.ubuntu.com/OperaBrowser#head-180d7c7b6dd969452592944e8dfd152d059c1708").[/QUOTE]
Errm, it's in the Gnome-Panel Menu, but the Icon files could not be installed for some reason or another.  I do forget the output message. Thanks though.

---

### Post by Perfect Storm on 2006-03-03
[QUOTE=Stereotypical Rage]To me Dapper is way more stable than Breezy was. Much much faster. ZOOM ZOOM!

 I've used every version of Ubuntu. Remembers the early days of Warty. :sniff: (Still a newbie though)[/QUOTE]

Perhaps, but I can't allow to take any chances :-/

---

### Post by ajgreeny on 2006-03-03
Sorry Zdravko.  I coppied the line for you to add then forgot to paste it in my reply a while ago.  How many of us have done that?  Apologies again but glad to see you've got it up and running as you wanted.

---

