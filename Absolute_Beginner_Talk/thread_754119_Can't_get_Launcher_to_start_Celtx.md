---
title: "Can't get Launcher to start Celtx"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Nodestar on 2008-04-13
I've finally installed Celtx, but now I've only found success running it through the terminal and only when using the Sudo command in front.

I also cannot start Celtx by double clicking on the Shell Script. 
When I do it brings up 3 commands
Run in Terminal
Run 
Display

None of these commands do anything. So I'm guessing thats why my Launcher isn't working.
These files are owned by Root. Not by me. Even though I am the master user on this PC(the only user for that matter)

Any help would be great.

---

### Post by zvacet on 2008-04-13
In your launcher under command must be path to the executable file.You will find it by browsing.Usualy it is in /usr/bin but I don´t know if that is the case with that program.

---

### Post by Nodestar on 2008-04-13
The Executable file is suppose to be a file in the celtx folder called celtx. Thats how some of the guides do it, so thats where I installed it. So on my Launcher the path is usr/local/celtx/celtx Only it doesn't work. 
Now when I browse there myself I can find this celtx file(Labeled a Shell Script) and click on it. I get 3 options as listen in my original post. None of them work. The only way I have started celtx so far is in the terminal with

Sudo /usr/local/celtx/celtx 

It prompts me for my password and then opens the program. I can't open it any other 
way.

---

### Post by isparkes on 2008-04-13
Hi Nodestar,

it's almost certainly a permissions problem.

Did you manage to remove the .celtx directory as in the other thread?

To get more infomation, open up a terminal manually, and execute the command from the command line. This will give you a chance to see the reason why it is not working. If you can tell us what it is saying, we can help some more...

---

### Post by Nodestar on 2008-04-13
Ok. I'm not sure what you mean. But I opened up the command line and typed /usr/local/celtx/celtx (leaving out sudo) and nothing happens. 

Also I tryed gksudo nautilus (from the other Post) and went into the celtx folder and made the "executable file" owned by me and gave my group (justin) access to read and write.

I put "executable file" in quotes because I've never got it to load up the program by it'self. So I can't confirm that it's even the right one. However everyone else says that it. celtx/celtx where celtx is a shell script.


Edit: Yes I deleted all the extra files including the .celtx

---

### Post by SlappyPappy on 2008-04-13
I have /usr/local/celtx/celtx for the command in my launcher and it opens right up.

Just curious how or where you installed celtx.

---

### Post by isparkes on 2008-04-13
You did exactly the right thing. It was that I wanted you to do - sorry if it was not clear.

OK, I am guessing the problem now is that although the celtx program has the right permissions and ownership, the things that it executes (a shell script is just a batch file - it won't do that much without calling on other programs) don't have the right permissions.

This is probably causing the shell script to bomb out, so that it croaks without any other news. Can you show the output of the following:

ll /usr/local/celtx

This should give you a bunch of information. If you can post a good portion of it here, perhaps I can see where the problem is.

I'm guessing that only the celtx shell script has the right permissions... The rest don't. (Only a guess at the moment).

---

### Post by isparkes on 2008-04-13
I downloaded celtx and untarred it.

The archive downloaded to the desktop. I did:

cd
cd Desktop
tar xvfz Celtx.tar.gz
cd celtx
./celtx

It ran right away.

I would suggest that you uninstall and try this - it should remove your permissions problems. If you want to go the full monty, try the following, which "virus protects" the installation by making it the property of root, and moving it to a suitable locaton (the /opt directory is one of the places that optional and non-official software is traditionally placed):

cd
sudo chown -R root:root celtx/
sudo mv celtx/ /opt

You can now run it using:

/opt/celtx/celtx

Hope this gets you on the road...

---

### Post by Nodestar on 2008-04-13
I installed it in usr/local/celtx/celtx  
I have that path in my Launcher and in my Applications. It just doesn't do anything.

I have alot of questions about the fileing system in Ubuntu. But I guess those are for another post. I was wondering if I should just uninstall and try putting Celtx in my Home Folder again. Although last time it didn't work. 
So one question. How do you uninstall a program like this? You just delete the Celtx folder in usr/local right?

I'll wait for a response before I do it because I know in windows not uninstalling unproperly will leave allot of left over files and I don't want that here.

justin@justin-laptop:~$ ll /usr/local/celtx
bash: ll: command not found
justin@justin-laptop:~$ 

Thats all I got from typing in that command,
I've also used gksudo nautilus and made the intire celtx folder owned by me. And given the group to me. And given me full use and read write priviledges. Still the same things as before.
To reiterate.
It works with Terminal Commands sudo /usr/local/celtx/celtx 
Double clicking on celtx/celtx file in the GUI brings up 3 options. All of which do nothing.
Launchers with correct path files do nothing. No error.. just nothing.

I'd like to learn more about the filing system.. should all programs like these be put in my home directory? What is the equevlant of Program Files from Windows, for Ubuntu?

By putting Celtx in a folder governed by root I make it virus protected because the files can't be altered or whatever unless someone was useing them logged in as Root?

I'd like all my installs to be nice and orderly but not sure how the filing system works. I'll keep reading Guides for now.

Thanks.

---

### Post by Nodestar on 2008-04-13
> **isparkes said:**
> I downloaded celtx and untarred it.

The archive downloaded to the desktop. I did:

cd
cd Desktop
tar xvfz Celtx.tar.gz
cd celtx
./celtx

It ran right away.

I would suggest that you uninstall and try this - it should remove your permissions problems. If you want to go the full monty, try the following, which "virus protects" the installation by making it the property of root, and moving it to a suitable locaton (the /opt directory is one of the places that optional and non-official software is traditionally placed):

cd
sudo chown -R root:root celtx/
sudo mv celtx/ /opt

You can now run it using:

/opt/celtx/celtx

Hope this gets you on the road...



I tried doing the 
cd
cd Desktop
tar xvfz Celtx.tar.gz
cd celtx
./celtx

I typed it all in and it seemed to work. But nothing happened.. I'm not sure where the files were unloaded to other than my desktop. I tried manually clicking on the celtx shell script file. Nothing happened like normal. I tried making a shortcut. Nothing happened.


I then tried this

cd
sudo chown -R root:root celtx/
sudo mv celtx/ /opt

And I didn't get past sudo chown -R root:root celtx/

Got this error

justin@justin-laptop:~$ cd
justin@justin-laptop:~$ sudo chown -R root:root celtx/
chown: cannot access `celtx/': No such file or directory
justin@justin-laptop:~$ 
 
I must be missing something very basic.. this is getting frustrating.

---

