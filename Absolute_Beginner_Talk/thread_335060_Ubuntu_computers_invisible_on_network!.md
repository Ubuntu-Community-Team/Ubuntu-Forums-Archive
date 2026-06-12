---
title: "Ubuntu computers invisible on network!"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by tickmike on 2007-01-09
Hi.
My 'Ubuntu Edgy Eft' computers are not showing up on my network ?. 

access the network ok, but cannot be seen from other Linux or windows machines on the home network..

Help please.
Michael.

---

### Post by scrooge_74 on 2007-01-09
Check your firewall, all ports are hidden and nobody can see it, for windows PC you need to enable samba so they can see it.

And this is a thread usefull for setting firestarter and samba  [http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138](http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138)

---

### Post by tickmike on 2007-01-10
Hi Scrooge_74. thanks for that link. I will look at that tomorrow .

My network is behind a Smoothwall box (firewall) This should have no affect on a Linux box ?.

Michael

---

### Post by scrooge_74 on 2007-01-10
No because your entire lan is behind it, if part was on the other side then you will have trouble

Just check that your linux box is letting the correct packets through so it can see the other PCs

---

### Post by tickmike on 2007-01-11
Hi .
I have had time to read the post on your link, and understand I have to make some changes....

# Allow response traffic $IPT -A INBOUND -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A INBOUND -p udp -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow response to netbios name broadcasts from the local network.
$IPT -A INBOUND -s $NET -p udp -m state --state NEW -j ACCEPT


In /etc/firestarter/inbound/setup     and  in a later post cuz said..

"the permissions for the /etc/firestarter/inbound folder and the setup file must be changed to writable before editing (and then, of course, changed back)."

 Q1 How do I access the folder to change, is it with 'Terminal' ?.
Q2 How do I change the permissions ..re cuz said.

Michael

---

### Post by scrooge_74 on 2007-01-11
to see which files are in that folder you can do sudo ls /etc/firestarter/inbound/

and should give you the list of the files, which are

allow-from  allow-service  forward  setup

to edit those files you only need to use your root privileges again, example if you want to modify the allow-from file

you can do from the firestarter directory sudo nano inbound/allow-from and you can make changes no problem, if you are not confortable with the command line you can do gksudo gedit /inbount/allow-from

You have write privileges when using the sudo command because you have the  administrator rights

---

### Post by tickmike on 2007-01-12
Hello Again.
I was working in 'nano' for another problem   .
And I put in at nano root      ls  /etc/firestarter/inbound/  But it said No such file or directory.  also get same results in Terminal by using 'sudo' first

Now what do I do ?

---

### Post by scrooge_74 on 2007-01-12
if I understand you right you did "nano root ls"?

if that is what you did is the incorrect command, is

"sudo ls the path to the directory"

and then sudo nano the path to the file you want to edit

---

### Post by tickmike on 2007-01-14
Hi .
I have tried this again with the same results      sudo ls /etc/firestarter/inbound/ 
  
   No such file or directory

Do I have to install or enable firestarter ?.
Michael.

---

### Post by kebes on 2007-01-14
First, to check if you have "firestarter" installed, open a [terminal]("http://psychocats.net/ubuntu/terminal") and type this:

```

dpkg --list | grep firestarter   

```

If, after pressing enter, it doesn't list anything, then firestarter is not installed. (If it is installed, you'll see something like "ii firestarter 1.0..3-1.1ubuntu4".)

To install firestarter you use the Synaptic Package Manager (Applications > Add Application) or you can type in a terminal:
```

sudo aptitude install firestarter

```

Once it's installed you can open firestarter by running the command "firestarter". This will give you a graphic interface to edit your firewall rules. You can then open up the ports you need to.

---

### Post by tickmike on 2007-01-14
Hi Kerbes, Thanks for that advice, It helped.
Firestarter was not on my system, I had to download  the software to my system, then installed it, that all went on ok.and I now have Firestarter running.  But..

Scrooge_74 said.....[B]to see which files are in that folder you can do sudo ls /etc/firestarter/inbound/

and should give you the list of the files, which are

allow-from allow-service forward setup[/B]

Yes I see that ok.

Next.

[B]to edit those files you only need to use your root privileges again, example if you want to modify the allow-from file

you can do from the firestarter directory sudo nano inbound/allow-from and you can make changes no problem
[/B]
I get GNU nano opened up but there are no files in it.?.
Also.
[B] if you are not confortable with the command line you can do gksudo gedit /inbount/allow-from
[/B]
I think you meant 'inbound' not 'inbount' anyway I tried them both.It just opens up the 'getit' viewer which is blank.no files showing.

Is it me doing something wrong ?.

Michael

---

### Post by kebes on 2007-01-14
Instead of trying to manually edit the firestarter configuration files, it is easier to use the firestarter GUI.

So do this:

1. Press "Alt+F2", which opens up the "Run..." dialog.

2. Type "firestarter" into the run dialog and click "Run".

3. When prompted, enter your password.

4. The firestarter GUI should now be open. You can go to the "policy" tab and add or edit rules as required.


This is the same as editing the config files, but is an easier way of doing it.

---

### Post by tickmike on 2007-01-15
I did this..

1. **Press "Alt+F2", which opens up the "Run..." dialog**.............Ok 

2.** Type "firestarter" into the run dialog and click "Run"**...........You have insufficient privileges.! , I got around this by clicking 'firestarter' from the drop down list(gksu firestarter). then Run ,  
3. **When prompted, enter your password.**      and that opened it up  ok.

4. **The firestarter GUI should now be open. You can go to the "policy" tab and add or edit rules as required.**

Its Greyed Out !!!  ?  ](*,)

---

### Post by kebes on 2007-01-15
Okay I'm sorry this is taking so long! ... now I understand why you were trying to make the changes to the files on the commandline. So, you're going to want to change the files:
/etc/firestarter/inbound/allow-from
/etc/firestarter/inbound/allow-service
/etc/firestarter/inbound/setup


To do this, open up a [terminal]("http://psychocats.net/ubuntu/terminal"), using the menubar:
Applications > Accessories > Terminal

Now, in the terminal, you would type:
gksudo gedit /etc/firestarter/inbound/allow-service

And then enter your password when prompted. You can then modify the file and you will be able to save changes afterwards. Follow the above procedure for any of the files you need to change. For your changes to "take effect" you may have to restart firestarter, by typing this in the terminal:
sudo /etc/init.d/firestarter restart


I hope that helps...

---

### Post by tickmike on 2007-01-15
Hi kebes,
You said..."**Okay I'm sorry this is taking so long**!" .... Well thank you very much for being patient with me.

what I have done ..
Terminal
sudo nautilus
file system
etc
firestarter
inbound
setup   right clicked..  permissions..tick 'write'  
display setup 
change file as 'dsmalley'  (added the last two lines)
................................................................................................................................
# Allow response traffic
$IPT -A INBOUND -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A INBOUND -p udp -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow response to netbios name broadcasts from the local network.
$IPT -A INBOUND -s $NET -p udp -m state --state NEW -j ACCEPT
----------------------------------------------------------------------------------------------

un write the permissions
reboot

looked from a windows machine and another ubuntu machine
DID NOT WORK still can not see that ubuntu machine
tried with the firestater off or on .. no good ..

Then noticed your last post.
you said ..

[B]Now, in the terminal, you would type:
gksudo gedit /etc/firestarter/inbound/allow-service[/B]

= blank page 

ok  I have just used the sudo nautilus method above and 'allow-service','allow-from' and 'forward' are empty blank files with no text in them....So I changed above "allow-service" to "setup"

[B]Now, in the terminal, you would type:
gksudo gedit /etc/firestarter/inbound/setup
[/B]
It opened the getit window and there was all the text file,  I rechecked my changes as I did with sudo nautilus method and it was ok.
also used your..sudo /etc/init.d/firestarter restart   but it still did not work .

O the joys of  Linux. It keeps the brain active !.
Michael..

---

### Post by scrooge_74 on 2007-01-15
Good excersize dont you think?  This will give us another advantage against window users when we get old. Our minds do a lot more excersize :D 

HAve fun

---

### Post by kebes on 2007-01-15
> **tickmike said:**
> but it still did not work .

Can you re-describe exactly the problem you're trying to resolve...?

In your very first post, you said:

> **tickmike said:**
> My 'Ubuntu Edgy Eft' computers are not showing up on my network ?. access the network ok, but cannot be seen from other Linux or windows machines on the home network.

But what do you mean "not showing up"? Note that if you simply use a Windows machine to "search the network" you probably won't see your Linux machine. Is there a specific service you are trying to establish? (File sharing? FTP? something else?)

I looked through the past posts but couldn't see exactly what connection you were trying to make... I apologize if I missed it.


So please describe exactly what you are expecting to see and what you are seeing instead. Modifying the firewall only works if you know exactly what type of things you are trying to let through!

---

### Post by scrooge_74 on 2007-01-15
The problem was the old tale of you have a network of computers to share files and printers and some computers dont show up even if you have SAMBA properly configure.

What happens is that you needd to do some manual changes to FIRESTARTER in order to be able to broadcast and get the names of the PCs to show up in the network manager be it either in Windows or in Linux when using SAMBA.

That is why we need to follow the [instructions in this thread]("http://http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138")

---

### Post by tickmike on 2007-01-16
Hello scrooge_74 and kerbes. I do think its good of you to help. :D 

Has I have come from windows, I have been used to seeing all the connected computers in 'my network places' and as you know you can then just click on one of your computers or workstations to access its resources ( as long as they are enabled and you have the correct permissions ) so looking for my two 'Linux (ubuntu) test machines 'on my network I thought there was a problem, being I could not see them.
At the moment I did not want to access them, just finding out why I could not see them.
But if I decide to make all of my home network ubuntu based then I would need to access these machines.

Scrooge_74   Your last link does not work, but is it this link you told me about earlier .

 [B]And this is a thread usefull for setting firestarter and samba   [http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138](http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138)
[/B]
This post by 'dsmalley' tells you how to get around this problem .
I have tried to follow his post and made the changes but alas it did not work for me.

Being my network is protected by a 'smoothwall box' do I really need this extra firestarter firewall ?.
Is there no way I can make the Linux box's show up on my other machines ?.
Michael.

---

### Post by scrooge_74 on 2007-01-16
It has been a while since I set up a Lan using win computers. And things are quite different with Linux.

In Linux if you open your cups system to let other PCs browse for your printers they basically come alive by themselve on your print manager.  As for checking files I do a conect to server and then use ssh (but you need to have the open ssh server working on the other machines), in that way I get an icon on my desktop pointing to that machine.  

I once had an icon pointing to a machine 10 kms away on another network and it was great.
You can also automatically mount drives that are in another machines, so if you get to config your LAN properly you can have a better network than you can with windows

On the firestarter thing, you are not really installing a firewall as you do in windows. Linux systems have built in security, Ubuntu comes close by default so you need to use a GUI interface to manage your firewall (believe you dont want to mess with IP tables unless you are good at it).  So in a sense is a good thing to have Firestarter install so you can check on your settings

---

