---
title: "What did i just do in the terminal.."
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by GodsDead on 2007-11-06
ok so, i installed XAMPP and it kept outputting errors when starting,
I typed in the errors in google and came across some foren site..
Didn't understand a word, but followed the terminal commands

it surprisingly fixed the xampp start problems, i just don't understand what i did, can someone please explain:


```

root@Spicy:/home/tom# nano /bin/arch
root@Spicy:/home/tom# chmod +x /bin/arch

root@Spicy:/# /opt/lampp/lampp restart
// i know that restarted xampp/lampp


```
Oh in as "su" i read that somewhere on the forums.. :S


and how can i "chmod" my htdocs directory do its easier for me to create and modify files without having to do it all through the bloody terminal?
And is there a way of changing the HTDocs directory? that might be easier..
as i have a spare slave HDD that i would prefer to have as the HTDOCS dir, then there's no matter about security.. since its whatever i put on that HDD!


Thanks!

---

### Post by Seisen on 2007-11-06
Nano is a text editor you open up the file that is located at /bin/arch and chmod + x basically gives permission for anybody to change the file located at /bin/arch.

---

### Post by scrooge_74 on 2007-11-06
> **GodsDead said:**
> ok so, i installed XAMPP and it kept outputting errors when starting,
I typed in the errors in google and came across some foren site..
Didn't understand a word, but followed the terminal commands

it surprisingly fixed the xampp start problems, i just don't understand what i did, can someone please explain:


```

root@Spicy:/home/tom# nano /bin/arch
root@Spicy:/home/tom# chmod +x /bin/arch

root@Spicy:/# /opt/lampp/lampp restart
// i know that restarted xampp/lampp


```
Oh in as "su" i read that somewhere on the forums.. :S


and how can i "chmod" my htdocs directory do its easier for me to create and modify files without having to do it all through the bloody terminal?
And is there a way of changing the HTDocs directory? that might be easier..
as i have a spare slave HDD that i would prefer to have as the HTDOCS dir, then there's no matter about security.. since its whatever i put on that HDD!


Thanks!

You can use the "bloody terminal" :lolflag: and type chmod (option) -R  /path_to_files/

so it changes the entire directory, in the long run I feel the terminal to be faster than moving the mouse

---

### Post by twiceasworn on 2007-11-06
The terminal is strange at first, but you slowly realize how much quicker and generally more powerful the terminal is over the GUI.  Linux itself is built AROUND the terminal.  So you should probably get used to it.  Trust me it is a boon more than it is a burden.

---

### Post by volksman on 2007-11-06
Wow..not to poop on anyone but lots of bad info in this thread.

Lets start with your question:

Looks like you created an empty file called /bin/arch.  This just silences the error which is looking for an app called arch (which really just barfs back your arch type).  This isn't a fix, it's a hack.  If you want it as a fix the file should contain the following:

```
#!/bin/sh

uname -m

```

> chmod + x basically gives permission for anybody to change the file located at /bin/arch.

Not entirely true.  chmod +x gives eXecutable privileges across the board on the file.  Meaning Owner,Group and World can execute the file as a script or binary (same idea as an exe in windows).  It doesn't give permission to change the file, just to run it.

As for terminal I would agree.  Get used to it.  Its EXTREMELY efficient and handy to have.

To change your htdocs dir so you can write direct do this:

```
sudo chown -R username.nogroup /opt/lamp/htdocs
chmod -R 775 /opt/lampp/htdocs
```

[COLOR="Red"]NOTE:[/COLOR]  Make sure you sub out "username" with your username.  If you didn't change the group that apache runs as then nogroup is correct otherwise put the right group after the period.

To change your htdocs location take a look at /opt/lampp/etc/httpd.conf or /opt/lampp/etc/extras/httpd-xampp.conf.  One of the two define the htdocs folder and you can change it accordingly.  You may want to install Webmin to make that a little easier to manipulate but personally terminal and vi (or nano) is the way to go.

---

### Post by GodsDead on 2007-11-06
OOps i forgot to mention that i did put 
uname -m 
in, but when i saved it, i didn't give it a file name?
but i didnt put in #!/bin/sh anywhere :S


thanks so much for the help, im getting started using linux, i think it will be cool to get into the terminal, since m a programmer anyways =p

and wow on the quick response lol! 


Now, could i use that same command to change the permission to this extra HDD i have formattted? (as when i access it /media/disk/ it wont let me do anything in there!)( i installed "partition editor?" and its set to ext2. is that ok?)

Then once i have permission to do things in that drive i can edit the http.conf file to point there ^__^

edit:
i used the same way as before..
```

sudo chown -R tom.nogroup /media/disk
chmod -R 775 /media/disk

```

And it kind of worked! it let me right click the folder & change some permission, see with the htdocs one, in the browser game a "forbidden" output, but changeing the files to "read" made this work =]

can i ask.. how comes i cant just chmod the folder?
does chown, have mroe functinos? so that you the query can be more specific?
:)

---

### Post by volksman on 2007-11-06
Actually all you would want to do is change the ownership not the execute bit.

So:

```
chown -R tom /media/drive
```

Tom being your user name (as per your first post... :) )

While the #!/bin/sh isn't 100% necessary I would advise you add that to the file.  And you gave it a file name when you issued:

```
nano /bin/arch
```

In a term when you call the app nano (or vi) and a file name after it it will either edit an existing file by that name or create a new one...So when you saved and exited the file arch was created in the /bin directory.

---

### Post by GodsDead on 2007-11-06
Ahh i get ya =]
Thanks volksman! youve helped me out a lot lol
Theres tonnes of things i still need to figure out on ubuntu ^__^ lol

Did you learn by just playing around?and asking questions? 
or is there a secret guide? =p lol


I take it my next step is to get "samba" to work, i installed it.. reading a post to network from a Micro$oft window$ Vi$ta...

just to i can move files from my vista to this machine, Would be ausom to setup shareing to that other HDD i now have permission to do things on =p

and so far i can gain access to "smb://beast/Public" which is my vista machine..

but i cant gain access from vista to my ubuntu machine.. :S


!! =]

---

### Post by volksman on 2007-11-06
Good to hear!  Glad I could help!

For Samba check out this how to  [http://ubuntuforums.org/showthread.php?t=202605&highlight=server](http://ubuntuforums.org/showthread.php?t=202605&highlight=server)

As for how did I learn?  Lots of reading, lots of mistakes leading to re-builds, and a massive hate on for MS.

Persistence is key....  :) 

Best of luck!

---

