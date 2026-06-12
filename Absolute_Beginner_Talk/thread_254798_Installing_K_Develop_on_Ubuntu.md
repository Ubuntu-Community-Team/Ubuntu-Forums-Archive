---
title: "Installing K Develop on Ubuntu"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by JrunkinDuncan on 2006-09-10
Ok I am an absolute beginner with linux in general, and Ubuntu as well.

Anyways,

I am trying to install k Develop for my Programming Class(C/C++) and I can't figure out how to install this thing. I downloaded the 3.3.4 Tar and extracted it to the Desktop and I am trying to install this thing. Now I am a complete Windows person so I am totally used their process of installation. 

So Can you guys give me a EXTREMELY SIMPLE Layout on how to install this thing. I have read the website and it says a part :

    $ export KDEDIR=/where/your/kde3/is
    $ export QTDIR=/where/your/qt3/is
    $ export LD_LIBRARY_PATH=$QTDIR/lib:$KDEDIR/lib:$LD_LIBRARY_PATH
    $ export LIBRARY_PATH=$QTDIR/lib:$KDEDIR/lib:$LIBRARY_PATH
    $ export PATH=$QTDIR/bin:$KDEDIR/bin:$PATH 

I don't know what half this stuff is. Thanks Alot.

-Dunc

---

### Post by Najand on 2006-09-10
This message  was deleted by the Author at 4:05 JST.

---

### Post by JrunkinDuncan on 2006-09-10
I have no idea how that was helpful Najand

---

### Post by sjhstorm on 2006-09-10
Kdevelop is in the repro's, so you can install using adept or apt-get.Current version in repro's is 3.3.4

---

### Post by Marsolin on 2006-09-10
[KDevelop]("http://linuxappfinder.com/package/kdevelop") can be installed through the Ubuntu repositories.  If you are using the 6.06 (dapper) release then the package name is "kdevelop3".  For the upcoming edgy release it will be "kdevelop".  If you can't find it you may need to use Synaptic to enable the universe repository section.  The lines should already exist, the comments just need to be removed.

---

### Post by JrunkinDuncan on 2006-09-10
Ok but how do I do this do I type that into the Terminal apt-get. 3.3.4? Or what. And as far as the Ubuntu Repositories, how do I Install from there. 

Thanks for the help and please I apologize for beind completely noob in this area. Thanks

---

### Post by JrunkinDuncan on 2006-09-10
Ok well this is great, now apt-get is broke!

E: Type 'apt-get' is not known on line 28 in source list /etc/apt/sources.list

is the error I get every time I try it either in the Terminal or the
Synaptic Package Manager.

How do I reset Apt-Get?

---

### Post by BombDiggity on 2006-11-09
What did you do to get that error?  Did you try and update your resource list?

to install kdevelop you should just go into the terminal and type

```
sudo apt-get install kdevelop
```

it should prompt you for your password and afterwards, it should insall and be ready for use.  as far as resetting the apt-get, not sure about that one.  

A general rule for Ubuntu and any Operating System, is before you edit anything that the system might rely on, you save a copy of the original on a thumb drive, or somewhere else on the computer.  

if apt-get doesn't work you can also try this:

```
sudo apptitude install kdevelop
```

apptitude is an alternative installation method in UBUNTU for terminal, so if you did break apt-get, you can always use apptitude and not worry about reinstalling anytime soon.

---

### Post by dwblas on 2006-11-09
> E: Type 'apt-get' is not known on line 28 in source list /etc/apt/sources.listYou have something like 'apt-get' in your /etc/apt/sources.list file.  Open it with a text processor and edit or delete the offending line.  If you want help with that, post the contents of the file.

---

