---
title: "total newbie"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by james1978 on 2007-06-19
hi guys my first post:p  I just installed ubuntu 7.04  and  to start  it looks really good and easy to use  but now that im all up an running  what would you say i need to learn now ?

---

### Post by LaRoza on 2007-06-19
Welcome, this is my 600th and something post :D. Well, what do you want to do? That usually precedes learning anything, unless you like to learn things for the sake of knowledge.

---

### Post by BHelts on 2007-06-19
personally, having been using ubuntu about 6 months now, if i got to do it over again, after installing the first thing i'd do (after getting all my settings/themes where i wanted them) would be to go to [Linux Command]("http://linuxcommand.org") and learn some of the basics of the terminal.

---

### Post by mahiyar on 2007-06-19
Learn the basic of linux / command line. There are lots of howtos on the web regarding that. If you have been stuck up in windows obviously you would have have been dependent on their applications as well like excel etc. Try learning their replacements like office.

---

### Post by james1978 on 2007-06-19
hi mate :p  Is installing  software  difficult ?  and is there certain programmes i can use to  guide me with installing stuff ?

---

### Post by LaRoza on 2007-06-19
If you are getting the programs through synaptic it will automatically download and install the software. You can get programs through Applications->Add/Remove programs, System->Administration->Synaptic, or through the command line. The command line is often easier.

---

### Post by ITdrummer on 2007-06-19
> **james1978 said:**
> hi guys my first post:p  I just installed ubuntu 7.04  and  to start  it looks really good and easy to use  but now that im all up an running  what would you say i need to learn now ?

I also am new to Ubuntu/Linux.  I have had Feisty installed now for a week and i love it!  The things i am doing with my new OS are:

1) Look through the add/remove programs list to see if there are any programs i might want/need
2) Learn the ins and outs of the OS
3) Figure out the differences between windows and linux (other than not sucking!)
4) Finding games that run on linux
And most of all:
5) Try to imagine most of the situations  you would regularly use your windows box for and make sure that you can do the same on your Ubuntu box.

As i said I am also a beginner so i am currently going through the same process you are.

(p.s. - learning the commands are a great help!)

---

### Post by BHelts on 2007-06-19
> hi mate  Is installing software difficult ? and is there certain programmes i can use to guide me with installing stuff ?

yes, there is Automatix2 and some may say it's the best thing out there.  I'd strongly advise against it however.  It messes with your sources.list.  There are also two graphical applications in Ubuntu to install programs.  Add/Remove Programs and Synaptic Package Manager.

Add/Remove Programs can be found in Applications menu.
Synaptic can be found at System ~> Administration

---

### Post by BHelts on 2007-06-19
if you want to learn to install programs through the command line use this a lot.  It'll help you find the correct name of the program.

```
sudo aptitude search [package name]
```

so for instance, if you want to install ubuntu restricted extras you could do 

```
sudo aptitude search ubuntu
```

and it will come up with ubuntu-restricted-extras so to install them (and all dependencies) which is nice

```
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by timzak on 2007-06-19
> **LaRoza said:**
> If you are getting the programs through synaptic it will automatically download and install the software. You can get programs through Applications->Add/Remove programs, System->Administration->Synaptic, or through the command line. The command line is often easier.

As a newbie myself (2 months and counting) I'd have to respectfully disagree with that.  Remember, you're speaking to a newbie.  I think for those who are out of their "newbieness" the command line is easier, but I've been using Feisty for 2 months and Synaptic and Add/Remove are both much easier/intuitive for me.  I like having a visual.  Add/Remove and Synaptic have categories, along with descriptions of the software as well as links to the software homepages.

My advice, from newbie to newbie, is to only install from Add/Remove and Synaptic until you have a good understanding of what you're doing from the command line.  The first days after installing Feisty for the first time, I received lots of advice on this forum giving me command line instructions exclusively.  I had no idea what I was doing, I just blindly followed directions.  I also had to reinstall Feisty a couple of times because I was blindly following advice without understanding what I was doing.  It took me a couple of weeks before I realized what Add/Remove and Synaptic were, and how easy they were to use (for me).  I wish my initial questions about installing software were answered by pointing me to Add/Remove and Synaptic.  When you get the hang of these, then you can start researching and experimenting with the command line more.  You will HAVE to learn the command line eventually...there's no getting around it in Linux, and once you gain a good understanding of it, you will enjoy working through it.

Good luck.

---

### Post by BHelts on 2007-06-19
timzak makes a very valid point.  i can't argue with it.  if you use add/remove or synaptic, make sure you have all sources enabled.
System ~> Administration ~> Software Sources and make sure they are all checked.

then in Add/Remove, make sure in the upper right next to show that "All Available Applications" is chosen.

that'll open up a lot more resources for you.

---

### Post by ejohn on 2007-06-19
i am a newbie to both linux and this forum...
i went through the linuxcommand website and pretty much have a grasp of at least the basic command as listed on that website. is bash scrpiting important? i mean is that high of priority when it comes to a newbie like me. what are the things that i should concentrate on?

---

### Post by hyper_ch on 2007-06-19
ejohn:

Well, linux has a very powerful command shell and unlike some previous poster said, the command line is often easier - also for newbies...
The reason is quite plain:
For the command line you just give out a command and there will be (mostly) an output... if that didn't help then the output gives further information...

However with a gui you have to guide a newbie through the whole gui and enabling this and that and that is very often more difficult. Especially if something isn't behaving as it should you have no output to give to the people that help you.

And the objection that you are given "wonderous" commands - it is up to you to either plainly follow them and copy'n'paste into the command shell or to figure out what they actually do. The documentation for the command line commands is extremly well.

E.g. someone tells you to
```

sudo chmod -R USER.USER /path/to/some/dir

```
You can enter that command and see what happens or you can try to understand what it does. By doing the second you also learn using the command line. To get to the documentation for a given command do this:

```

man COMMAND

```

For the above example do:
```

man sudo

```

And then maybe
```

man chmod

```

To leave the man pages press "q"


With regards to bash scripting:
You will see that repetitive tasks you do can be easily scripted - that will take work off your time...
What I did for example is an installation script that will sort of default setup my computer in case I do reinstall Xubuntu.
It took some time to write it but if I need it, a reinstall will be very quick ;)

---

