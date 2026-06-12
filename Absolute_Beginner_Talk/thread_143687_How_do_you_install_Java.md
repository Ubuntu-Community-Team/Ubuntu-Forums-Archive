---
title: "How do you install Java ?"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by snooker on 2006-03-12
Hello . I'm new here , Would like to know how do you install Java onto this operating system ? 

TIA !

---

### Post by Zelut on 2006-03-12
have you tried searching for java using Synaptic?  You may need to enable universe & multiverse repositories by going to Settings > Reporitories > Add > Enable Multiverse & Universe.

Give that a try.

---

### Post by snooker on 2006-03-12
No I haven't try that , what is universe & multiverse repositories ? 

TIA

---

### Post by Zelut on 2006-03-12
programs are downloaded and installed from different 'repositores' which are seperated by class.  there is a security 'repo', main, backport, multiverse, universe... pretty much the multiverse & universe repos are packages developed by the community..

---

### Post by jchutcheson on 2006-03-12
I'm having the same problem

---

### Post by Zelut on 2006-03-12
Also pretty sure you can find a .bin file for download at the java website & install it that way.  

[http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp)

Try that link..

---

### Post by snooker on 2006-03-12
Ok I will try that webpage but what does it mean when it say " Save on Disk " ? Does that mean on the hard drive ?

---

### Post by jchutcheson on 2006-03-13
Hi ... These repositores , Should they all be enable ? Also could you explain how to do this >>> Make the downloaded file executable. At the command line, change to the directory where you downloaded the file, and type >>>> chmod +x jre-1_5_0_06-linux-i586.bin  <<<

---

### Post by Madpilot on 2006-03-13
Information on Ubuntu's repositories: [http://wiki.ubuntu.com/AddingRepositoriesHowto](http://wiki.ubuntu.com/AddingRepositoriesHowto)
For Java, see the Java section here:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

That chmod +x line needs to be typed in a terminal, after you use 'cd' to move to the directory you downloaded the jre bin file to.

[https://wiki.ubuntu.com/BasicCommands](https://wiki.ubuntu.com/BasicCommands) has some basics on the terminal.

---

### Post by mlind on 2006-03-13
if you search the forums, you'll find plenty of different ways to install Sun's java
environment.

I prefer doing it using java-package, instructions can be found [here]("http://www.debian-administration.org/articles/142"). You need
to enable *multiverse* repository to get java-package.

---

### Post by gmclachl on 2006-03-13
I know I rolled my own Java package, as have many others I am sure. It's fairly easy to do if you follow the instructions on the Wiki. Unfortunately  AFAIK it would be impossible for me, or anyone else, to make this package available as there is an issue with Sun's licensing .

George

---

### Post by jchutcheson on 2006-03-13
[QUOTE=Madpilot]Information on Ubuntu's repositories: [http://wiki.ubuntu.com/AddingRepositoriesHowto](http://wiki.ubuntu.com/AddingRepositoriesHowto)
For Java, see the Java section here:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats).[/QUOTE]

Hi ... The above part I have done , Its this below part that I am confuse with , I understand it about codes and using the Terminal to locate files and folders but , What I am not understanding is in the Terminal section part what do I need to type to install the Sun java program ? When I downloaded , I selected to save on disk , So Its on my computer somewhere , What command does it take to load it now ? Also in the terminal area , If I type cd nothing happen , Any help much appreciated , Thanks 

That chmod +x line needs to be typed in a terminal, after you use 'cd' to move to the directory you downloaded the jre bin file to.

[https://wiki.ubuntu.com/BasicCommands](https://wiki.ubuntu.com/BasicCommands) has some basics on the terminal.[/QUOTE]

---

### Post by hod139 on 2006-03-13
I wrote a howto for installing java [here]("http://ubuntuforums.org/showthread.php?t=140769").  I think this is the easiest way to do it, let me know if anything isn't clear (post questions in the howto thread though so others can benefit.)

---

### Post by jchutcheson on 2006-03-13
Hi ... I am asking here because I really need to know the basic , From your post ? It seem you are providing the methods that needs to be done to install the program but where is the direction to getting there to start them ? Where do you go to perform them ? I know where the repositories is located and I have everything in there set to enable too , Your methods ? Do I go to the terminal and just copy and paste your codes ??? ...Thanks 

I am really surprise for something that should be easy to perform isn't ...

---

### Post by Griff on 2006-03-13
NOOOO!!! Sorry for the dramatics, but the JAVA runtime environment and/or the JAVA development kit can be installed with arnieboy's Automatix.  I've installed JAVA from the sun JAVA site and from Automatix and the latter is a huge time saver.

Check out Automatix Here:[http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix)

Note: Automatix can install many many things if you desire! Just look at the list! Beautiful!

---

### Post by hod139 on 2006-03-13
[quote=Griff]
I've installed JAVA from the sun JAVA site and from Automatix and the latter is a huge time saver.
[/quote]

There is nothing wrong with using Automatix and it does simplify a lot of stuff, but sometimes I prefer to do things myself.  

[quote=jchutcheson ]	Hi ... I am asking here because I really need to know the basic , From your post ? It seem you are providing the methods that needs to be done to install the program but where is the direction to getting there to start them ? Where do you go to perform them ? I know where the repositories is located and I have everything in there set to enable too , Your methods ? Do I go to the terminal and just copy and paste your codes ??? ...Thanks
[/quote]
I"m not entirely sure what you are asking.  For step one of my howto, you have to edit the sources.list file located at /etc/apt.  You can use your favorite text editor to do this.  If for example you like gedit you would open a terminal and type:
```

sudo gedit /etc/apt/sources.list 

```
and add 
```

## http 100mbit/s mirror provided thanks to OVH [http://ovh.com]("http://ovh.com/")
deb [http://packages.freecontrib.org/ubuntu/plf/]("http://packages.freecontrib.org/ubuntu/plf/") breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/]("http://packages.freecontrib.org/ubuntu/plf/") breezy free non-free
``` to the bottom (doesn't really matter where) of the file.

After that, you run ```
sudo apt-get update
``` and then follow the desired step 2 (JRE or SDK).  Following those steps is simple copying and pasting the commands.  Hope this helps.

---

### Post by jchutcheson on 2006-03-13
You know Griff I wish someone would of told me about this , I am assuming its a program " Automatix " its easy to install , its easy to select programs , It would of saved me alot time and headaches , THANK YOU big time ....

You see in my line of work I find used computers for free and most of time they are in pretty good shape , though they aren't anything special usually P2 or P3 units , I would fixes them up so that they can be used with windows but, Thats where the problems is sometime , The people that I usually sell them to don't want to spend money on a OS (  windows ) and I don't blame them , They only want tpo use them for surfing the web , emailing others and chatting in messenger ,thats it , They don't use it for anything personal stuff , they don't care for paid softwares or whether they get viruses , I usually sell them for $50 a unit ... 

Again I thank you !!!

---

### Post by Madpilot on 2006-03-13
[QUOTE=jchutcheson]Hi ... The above part I have done , Its this below part that I am confuse with , I understand it about codes and using the Terminal to locate files and folders but , What I am not understanding is in the Terminal section part what do I need to type to install the Sun java program ? When I downloaded , I selected to save on disk , So Its on my computer somewhere , What command does it take to load it now ? Also in the terminal area , If I type cd nothing happen , Any help much appreciated[/QUOTE]

Assuming you're using Firefox,  it uses the /Desktop folder to download stuff to.

So, open a terminal (Applications->Accessories->Terminal) and type:
```

cd Desktop

```
Note the capital D in Desktop - case matters in the terminal.

Then run the rest of the commands you've been given - chmod +x, etc - and you'll get Java running without having to inflict Automatix on your machine.

---

### Post by jchutcheson on 2006-03-13
[QUOTE=Madpilot]Assuming you're using Firefox,  it uses the /Desktop folder to download stuff to.

So, open a terminal (Applications->Accessories->Terminal) and type:
```

cd Desktop

```
Note the capital D in Desktop - case matters in the terminal.

Then run the rest of the commands you've been given - chmod +x, etc - and you'll get Java running without having to inflict Automatix on your machine.[/QUOTE]

You see that doesn't work , Yes I do have the Sun Program downloaded on the desktop and in the home folder , I have 2 of them there just incase If I could try from there , Yes I have everything enable in the repo and yes i made sure to update , follow by a reboot but , when I try from the terminal ? Even if I copy and paste or type it in , doesn't matter still the same results , fail ... It would seem getting the correct command line the major problem 

Thanks for Griff idea is the only thing that has work

---

