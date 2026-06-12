---
title: "losing patience with this avg wont install or uninstall"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by duderduderini on 2007-06-04
Hi
Yes i read the article on how to install avg
yes i went to grisoft to install it
no it wont work
i try to uninstall i get an error message (screenshot2.png)
i tried to install i get this( screenshot.png)
I have been at this for a month now and i havent even mentioned getting my canon n650u scanner to work.
Unfortunately windowsxp is looking good again
If anyone can help me I would really value it
Cheers
Nick

---

### Post by pawitp on 2007-06-04
I'd rather think that this is a problem with AVG and ubuntu has no control over this.

---

### Post by starcraft.man on 2007-06-04
Aye, I like AVG but I seen quite a bit of problems with it on Ubuntu. May I ask why you want an AV installed? You don't need to worry about viruses, you won't get any... Oh and if this is for scanning mail before sending to windows machines (only real purpose for an AV on Linux) you might wanna check out [ClamAV]("http://www.clamav.net/").

To install just open terminal (Applications > Accessories > Terminal) and type in "sudo aptitude install clamav". Or if you like GUI, go System > Administration > Synaptic Package management > Search > clamav. Then just check and install it.

Anyway, is there a particular reason you need an AV?

---

### Post by duderduderini on 2007-06-04
I find the complacency with viruses a bit disarming to be frank amongst linux users. I mean its possible isnt it? Anyway i cant get avg off my pc now can i? I am soooo frustrated with trying to rid myself of windows. I almost did it at work bar 2 programms and then today firefox updated itself and noew i cant listen to internet radio...
Anyway back to the topic at hand..
Can i uninstall it at all do you think ?
Then
what do you know about scanners?
Thanks for your help i really do appreciate it
Nick

---

### Post by mywildyears on 2007-06-04
I'm sure its possible to get a virus in ubuntu, but the likeliness of it actually happening is probably a million to one.  The reason is simple: Windows systems get viruses because the majority of computer users run Windows.  A person creating a virus won't affect any users if they create it for GNU/Linux (or very few).  My advice is to just forget the virus scanner all together.  You won't have to worry about viruses.

---

### Post by Cypher on 2007-06-04
> **duderduderini said:**
> I find the complacency with viruses a bit disarming to be frank amongst linux users. I mean its possible isnt it? Anyway i cant get avg off my pc now can i? I am soooo frustrated with trying to rid myself of windows. I almost did it at work bar 2 programms and then today firefox updated itself and noew i cant listen to internet radio...
Nick
I wouldn't call it complacency on the Linux users part as much as confidence in the knowledge that there are very few viruses that target the Unix/Linux environment to begin with and the general structure of a Linux system makes taking over the system a lot harder.

Ubuntu basically forces you to login as a regular user with limited rights to files just within your home directory. If you need to do anything on a system level, you must provide the root password. So if a virus were to come into your system, it would at best attempt to damage the files in your home directory, for everything else it would need the root password.

Additionally Linux's lack of a Windows registry type interface means that viruses can't inject things that ensure programs start up when they need to and so on.

I've been using Linux based system for almost 10 years now and have bothered with a virus scanner on any of the distro's I've used, whereas it's the first thing I put on a brand new Windows installation before attempting to do anything on the Internet.

Now as far as the issue at hand, it looks like there are some coding errors in the scripts for the AVG package.

Can you open up a terminal by going to Applications->Accessories and type
```

dpkg -l | grep avg
sudo apt-get purge <package>

```
Where <package> is whatever the package name is you gleaned off the first command. If the "apt-get" command doesn't properly work you can try
```

dpkg --force-all -P <package>

```

---

### Post by rich.bradshaw on 2007-06-04
There are no Linux viruses in the wild.

Loads of webservers run apache+linux, so the argument that most people run Windows is bunk. A virus that could bring down linux+apache would bring down a lot of the internet.

Most linux anti-virus is supplied so that you don't accidentally send viruses to windows users.

Linux is not vunerable to viruses in the same way due to the robust permissions architecture that it uses. 

To get a virus you would have to:

1) Download it
2) chmod +x virusfile
3) ./virusfile
4) It would likely fail, as it would need root permissions
5) sudo ./virusfile
6) enter your root password
7) Congratulations - you are now infected. You can now give these instructions to your friends so they can be infected too.

In windows this procedure goes like this:

1) Internet Explorer automatically allows an unsigned activeX control or downloads an exe without you knowing.
2) It is already executable, and you are already root.
3) You are infected.

There are some differences there, notable, files aren't automatically executable in linux, and that you can't mess things up without being root.

---

### Post by Carlos Santiago on 2007-06-04
Dude, to remove AVG open a terminal and type:
sudo dpkg -R -P avg75fld 

However, if you expect to have exactly the same programs you have in windows, is better to stay with it.

To switch to linux you have to be open mind and expect that in Linux you have different programs, with different features (usually much more ;-) ).

For example, in windows you download your programs from some "expected to be trustable site", and then double click and install. Then you have to register the program and pay for them (at least you supposed to)
And you have to repeat this procedure for every program you want to install.

Here you search your programs from a trustable source and select the programs you want to install.
Then you just have to click install button. You install them all with 1 single click !!!!!!!!!!!!

Notice that here you have supported and the unsupported programs. Usually all of them work, but of course unsupported programs may be more difficult to configure. The AVG is  NOT supported by Cannonical!

---

### Post by johnz8 on 2007-11-03
> **duderduderini said:**
> Hi
Yes i read the article on how to install avg
yes i went to grisoft to install it
no it wont work
i try to uninstall i get an error message (screenshot2.png)
i tried to install i get this( screenshot.png)
I have been at this for a month now and i havent even mentioned getting my canon n650u scanner to work.
Unfortunately windowsxp is looking good again
If anyone can help me I would really value it
Cheers
Nick

I am sort of in the same boat. AVG shows up in my Applications drop down box under accessories but it wont let me update or use it. It says It needs root. I tried everything I could think of to give it permission but no deal. So then I decided to just use add/remove to get rid of the freaking beast but AVG does not show up on the add/remove list in any way. I am too new at this to simply go pick out the files and figure out how to remove the icon from the drop down. I am screwed unless someone can help here.:(

Help!

---

### Post by por100pre1 on 2007-11-03
> **johnz8 said:**
> I am sort of in the same boat. AVG shows up in my Applications drop down box under accessories but it wont let me update or use it. It says It needs root. I tried everything I could think of to give it permission but no deal. So then I decided to just use add/remove to get rid of the freaking beast but AVG does not show up on the add/remove list in any way. I am too new at this to simply go pick out the files and figure out how to remove the icon from the drop down. I am screwed unless someone can help here.:(

Help!

AVG's last version is buggy, you can try running its command with sudo; but IMHO, you'll do better trying avast instead.

---

