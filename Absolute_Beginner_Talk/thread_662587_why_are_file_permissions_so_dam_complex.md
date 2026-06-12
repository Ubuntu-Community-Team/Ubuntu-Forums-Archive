---
title: "why are file permissions so dam complex"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by circusmonkey on 2008-01-09
Im by no means an expert or programmer but geeez talk about making life hell for those of us who not experts with linux .... I installed an application it creates a folder in my home directory which now has a fat padlock on. After looking at various threads and the help on file permissions I am still in the dark , why on earth can I not just right click on a folder and set a permission ! it would make life so much easier !  

So I have to type some code in a terminal , the folder with the padlock  is home/robert/houdini9.1  when I installed the application I used sudo ./houdini.install  . 

baffled.....

R

---

### Post by gn2 on 2008-01-09
Do you need access to the folder, or is the padlock to stop you from messing it's configuration files up?
If you absolutely have to access the folder, Alt+F2 then  gksudo nautilus

[COLOR="Red"]This gives unrestricted access to all files with root permissions, so be very careful what you do.[/COLOR]

---

### Post by meindian523 on 2008-01-09
Well,you CAN right click a folder and set it's permission IF you are the owner.

Actually,permissions are not too complex,maybe you didn't pay attention while you were reading the threads?

---

### Post by mister_pink on 2008-01-09
> **circusmonkey said:**
> Im by no means an expert or programmer but geeez talk about making life hell for those of us who not experts with linux .... I installed an application it creates a folder in my home directory which now has a fat padlock on. After looking at various threads and the help on file permissions I am still in the dark , why on earth can I not just right click on a folder and set a permission ! it would make life so much easier !  

So I have to type some code in a terminal , the folder with the padlock  is home/robert/houdini9.1  when I installed the application I used sudo ./houdini.install  . 

baffled.....

R

If anyone could just click on the file and change its permissions then you might as well not bother having them. I can understand that at first they seem a little complex but once you get used to them its easy really. They're one of the reasons that people say linux is secure - in windows if you log in as admin then you and any program that you run has the ability to do anything to your system. By restricting your own access you restrict what damage a malicious or badly coded program can do. But to cut to the chase, check this out: [http://catcode.com/teachmod/](http://catcode.com/teachmod/)

---

### Post by circusmonkey on 2008-01-09
Do>  you need access to the folder, or is the padlock to stop you from messing it's configuration files up?
If you absolutely have to access the folder, Alt+F2 then sudo nautilus

well I know the application places files in the folder and alters  settings for the application etc etc , its like a users settings are contained there. Just like my documents in windows. so I presumed if I log in as robert , and using the application , if the folder is locked the application cannot add or alter files within the folder. 

> Well,you CAN right click a folder and set it's permission IF you are the owner.

Actually,permissions are not too complex,maybe you didn't pay attention while you were reading the threads?

Surely I am the owner , its my home directory. I am the only user , I dont think its got anything to do with paying attention , its more like I don't understand .....


> f anyone could just click on the file and change its permissions then you might as well not bother having them. I can understand that at first they seem a little complex but once you get used to them its easy really. They're one of the reasons that people say linux is secure - in windows if you log in as admin then you and any program that you run has the ability to do anything to your system. By restricting your own access you restrict what damage a malicious or badly coded program can do. But to cut to the chase, check this out: [http://catcode.com/teachmod/](http://catcode.com/teachmod/)

thanks for the link , I can see the point of security , lets hope I can fix my fix my folder with ease ! 

Rob

---

### Post by meindian523 on 2008-01-09
The installer created the folder,not you,therefore the folder is owned by whoever ran the installer,namely root,so even though it's in your home directory,you are NOT the owner.

---

### Post by Paqman on 2008-01-09
> **circusmonkey said:**
> talk about making life hell for those of us who not experts with linux .... 

On the plus side, permissions also make life hell for viruses. The difference is that you'll learn to deal with permissions pretty soon, while the viruses will still be foiled by them.

Permissions are a really good thing.

---

### Post by gn2 on 2008-01-09
If you "gksudo nautilus" as I suggested you should be able to right-click on the folder and change the owner and file permissions in Properties>Permissions then exit Nautilus.

(works that way in Xubuntu with Thunar.....)

Remember the warning applies regarding root permissions......

---

### Post by circusmonkey on 2008-01-09
with ls -l

drwxr-xr-x 5 robert robert   4096 2007-10-26 13:33 houdini9.0
drwxr-xr-x 2 root   root     4096 2008-01-08 20:07 houdini9.1

after following the link and having a quick read I thought 

chmod u=rwx houdini9.1 would work , but instead I get chmod: changing permissions of `houdini9.1': Operation not permitted 

this did not work either 

robert@circusmonkey:~$ chmod og=wrx houdini9.1
chmod: changing permissions of `houdini9.1': Operation not permitted


On the other hand 

> If you "sudo nautilus" as I suggested you should be able to right-click on the folder and change the owner and file permissions in Properties>Permissions then exit Nautilus

this worked like a dream !!! quick easy no messing for a linux noob

---

### Post by meindian523 on 2008-01-09
I told you that directory is owned by root,that's why you are not able to edit it's permissions.

To work around the problem use ```
sudo chmod bla bla
```

---

### Post by Paqman on 2008-01-09
Glad you've sorted it. Do you understand why that worked? It was because you used nautilus as root (using sudo) whereas the command you entered was with your normal priviledges. If you'd prefixed the command with sudo it would have worked, too.

Btw, for GUI programs like nautilus you should use gksudo instead of sudo. Sudo will work, but gksudo is preferred (for obscure technical reasons)

---

### Post by Don9307 on 2008-01-09
Well, you can begin by spelling the explative with an "n.'

---

### Post by shahab.fm on 2008-01-09
the problem is you are not logged in as root ... you have to use :

sudo chmod og=wrx houdini9.1

sudo keyword makes you root in UBUNTU ( correct me if i am wrong ) , in other distributions you should login as root first with the command 

su

enter password for root

NOW YOU ARE ROOT :-)

but in Ubuntu that's enough just to add sudo at the first place of your command.

Have fun with Linux, it is easy just be patient and GOOGLE all :guitar:

---

### Post by hyper_ch on 2008-01-09
Two good resources:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bbqsandwich on 2008-01-09
> **Don9307 said:**
> Well, you can begin by spelling the [SIZE="4"]explative[/SIZE] with an "n.'

;-)

---

### Post by geirha on 2008-01-09
> **circusmonkey said:**
> So I have to type some code in a terminal , the folder with the padlock  is home/robert/houdini9.1  when I installed the application I used sudo ./houdini.install  . 

If you're installing something to your homedir, you don't need root privileges, so if you'd omitted sudo in front of that command, you wouldn't have had any problems with permissions.

---

### Post by meindian523 on 2008-01-09
LOL.I noticed that too,but if we go posting about grammatical errors,I would be called a troll,hungry for beans and maybe even the beans I accumulated really helping people out would be withdrawn.... :(Seriously,I'm amazed by the grammar and spelling mistakes made by people who have English as their native language!

---

### Post by Shadows_Fall on 2008-01-09
You can also just open your terminal, and type: sudo chown username:group /path/to/folder
EX: sudo chown robert:robert /home/robert/mydir

That will set you as the owner of the folder.

---

### Post by bodhi.zazen on 2008-01-09
> **circusmonkey said:**
> Im by no means an expert or programmer but geeez talk about making life hell for those of us who not experts with linux .... I installed an application it creates a folder in my home directory which now has a fat padlock on. After looking at various threads and the help on file permissions I am still in the dark , why on earth can I not just right click on a folder and set a permission ! it would make life so much easier !  

So I have to type some code in a terminal , the folder with the padlock  is home/robert/houdini9.1  when I installed the application I used sudo ./houdini.install  . 

baffled.....

R

Ownership and permissions is unrelated to programming. Every OS, even Widows, has ownership / permissions. It is a reality of the modern internet security and disabling such basic security has obvious detriments.

If you are new to a OS, you will find even the most basic "simple" tasks difficult. As you become familiar with the OS it will not seem so difficult.

So ...

1. If you want to learn a new OS it is best approached with an open mind and be prepared to learn.

2. The terminal or CLI is not programming, it is a (Bash) shell. Yes you can write Bash scripts if you like. There is a difference between system administration and programming.

3. It is a common mistake to confuse "familiar" with "easy" or "simple" or "just works". Do not fall into this misunderstanding.

4. Many people use Linux (without doing programming or system administration) as easily s they use Windows.

5. Many people find Linux is preferable to other OS once they learn the basics. You need to be partint with yourself and a new OS.

6. If you are having problems, that is what the Forums are designed to help with. Feel free to come on back.

7. Many people find Linux is not for them. If that is the case, good luck to you and come on back if you ever change you mind. No need to rant.

---

### Post by gn2 on 2008-01-09
> **bodhi.zazen said:**
> 
2. The terminal or CLI is not programming.

Neither is it simple or straightforward.

Point and click does the trick!

CLI useful to have for emergencies though.

---

### Post by hyper_ch on 2008-01-09
terminal and CLI are simple and straight forward....

Point and click various hugely amount different desktop environments ;) that is not simple or straightforward.

CLI is just a one-in-all solution ;)

---

### Post by gn2 on 2008-01-09
> **hyper_ch said:**
> terminal and CLI are simple and straight forward....

Point and click various hugely amount different desktop environments ;) that is not simple or straightforward.



But you can usually find your way around with a mouse and explore things and find what you are looking for.

If you don't know beforehand what text to input the CLI is utterly useless.

---

### Post by hyper_ch on 2008-01-09
you also can do exploring of the shell

---

### Post by circusmonkey on 2008-01-09
> If you're installing something to your homedir, you don't need root privileges, so if you'd omitted sudo in front of that command, you wouldn't have had any problems with permissions.

What a great tip !. When I installed the application I followed a documented tutorial , which was done obviously because of the complex nature of installing the application. If I had known all of these commands/ tips there would of been no problems !. I do have a very open mind  to using / learning  but its the frustrating nature of not  knowing what is wrong in the first place and then having to be able to call commands up to fix the problem which I could never of found in the help , due to not knowing what I was looking for in the first place ..............

So now I have a large collection of notes in a text file which I have to refer to ! 


Thanks all for the help 

R

---

### Post by bodhi.zazen on 2008-01-09
LOL

The mouse is convenient and some users have no need for the CLI.

/bodhi bows to the Macintosh gods (NOT WINDOWS) for bringing us the modern gui

BUT ... the mouse method may fail for a variety of reasons and a majority of servers are managed (best) from the command line and a few config files.

The command line is intimidating at first, but I would encourage everyone to learn the basics of the CLI. It is simple, enter a command and it runs. One thing nice is once you have the basics down, learn how to navigate the man pages, you can sys admin almost any *nix box as 80% + is common enough across distros.

Again, not to beat a dead horse, assuming you are not familiar with the command line, don't make the mistake of assuming the unknown is harder or more complex.

It is easier to give instruction on the forums in CLI commands for obvious reasons (it is easier to type a few commands then describe mouse clicks and buttons, plus if the command fails the error message is often helpful for debuging even if the OP does not understand the output).

To each their own, whatever works, it is all good.

---

### Post by hyper_ch on 2008-01-10
> **bodhi.zazen said:**
> /bodhi bows to the Macintosh gods (NOT WINDOWS) for bringing us the modern gui

Shouldn't you bow to Xerox for the mouse and gui?

---

### Post by gn2 on 2008-01-10
Like many technological advances, radar etc, the GUI was created by developement during warfare, in the case of the GUI, it was the Cold War.
The first GUI was the display for the SAGE defence system:
[http://en.wikipedia.org/wiki/SAGE_Project](http://en.wikipedia.org/wiki/SAGE_Project)

---

### Post by hyper_ch on 2008-01-10
didn't know that... but the mouse was a Xerox invention, right?

---

