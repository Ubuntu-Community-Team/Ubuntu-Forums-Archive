---
title: "tremulous .run file"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-04-27
I cant acsess this file, when i double click on it, it says 
Could not open the file /home/alan/Desktop/tremu…s-1.1.0-installer.x86.run.
Please help!

---

### Post by Outrunner on 2007-04-27
go intro the terminal and type
```

sudo ./home/alan/Desktop/tremulous-1.1.0-installer.x86.run
```

---

### Post by mojo123 on 2007-04-27
alan@alan-laptop:~$ sudo /home/alan/desktop/tremulous-1.1.0-installer.x86.run
sudo: /home/alan/desktop/tremulous-1.1.0-installer.x86.run: command not found

---

### Post by Outrunner on 2007-04-27
> **mojo123 said:**
> alan@alan-laptop:~$ sudo /home/alan/desktop/tremulous-1.1.0-installer.x86.run
sudo: /home/alan/desktop/tremulous-1.1.0-installer.x86.run: command not found

Copy and paste my command into the terminal. There's a "." before /home/...

---

### Post by mojo123 on 2007-04-27
alan@alan-laptop:~$ sudo ./home/alan/Desktop/tremulous-1.1.0-installer.x86.run
sudo: ./home/alan/Desktop/tremulous-1.1.0-installer.x86.run: command not found

---

### Post by stevenrushing on 2007-04-27
capitalized Desktop?

---

### Post by mojo123 on 2007-04-27
its not suppose to be?

---

### Post by Outrunner on 2007-04-27
Can you right-click the file and select 'Run in terminal...'?

---

### Post by Seisen on 2007-04-27
Try this

```
sudo sh /home/alan/desktop/tremulous-1.1.0-installer.x86.run
```

---

### Post by Outrunner on 2007-04-27
ohh yeah I think you're supposed to do 

```
sudo chmod 755 /home/alan/Desktop/tremulous-1.1.0-installer.x86.run
```

first

---

### Post by mojo123 on 2007-04-27
sudo sh /home/alan/desktop/tremulous-1.1.0-installer.x86.run
sh: Can't open /home/alan/desktop/tremulous-1.1.0-installer.x86.run

---

### Post by Seisen on 2007-04-27
Try it without putting sudo in front of it.

---

### Post by Outrunner on 2007-04-27
> **mojo123 said:**
> sudo sh /home/alan/desktop/tremulous-1.1.0-installer.x86.run
sh: Can't open /home/alan/desktop/tremulous-1.1.0-installer.x86.run

Try my command and then do Seisen's again.

---

### Post by aktiwers on 2007-04-27
Also Tremulous is in the repos:

```
sudo apt-get install tremulous
```and it should be installed. Then you can either start it by typing:
```
tremulous
```Finding it in your games folder in the main menu.


If you really want to install from that file, you should do as Seisen says:> 
sudo sh /home/alan/desktop/tremulous-1.1.0-installer.x86.runQutrunner:
Isnt that what you have to do for .bin files?

EDIT:
Proberbly also .run files then? :)

---

### Post by mojo123 on 2007-04-27
nop doesnt say run in terminal 
fixed thx aktiwers

---

### Post by Seisen on 2007-04-27
[http://linuxmonitor.net/blog/2007/03/tremulous-best-open-source-game-ive.html]("http://linuxmonitor.net/blog/2007/03/tremulous-best-open-source-game-ive.html")

Here is a link that should help

---

### Post by Outrunner on 2007-04-27
> **aktiwers said:**
> Isnt that what you have to do for .bin files?

EDIT:
Proberbly also .run files then? :)

I'm fairly certain that it works for .run files aswell but I might be wrong.

> **mojo123 said:**
> nop doesnt say run in terminal

Ok, but do this: sudo chmod 755 /home/alan/Desktop/tremulous-1.1.0-installer.x86.run

---

### Post by hyperair on 2007-04-27
just do a 
```

sudo chmod +x /home/alan/Desktop/tremulous-.1.1.0-installer.x86.run

```

That gives it permission to execute.

---

### Post by mojo123 on 2007-04-27
i fixed it

---

### Post by Sweet Spot on 2007-05-22
Time to revive a 3 week old thread: I can really use some help with this as I'm having issues installing. Basically, I can't. :(  It's NOT in the repos for me, and I do have all of the repositories enabled. Perhaps it's because I'm still using Dapper ?   So I have the 1.0 x86 run installer on my desktop, and I've tried every single method listed in this thread to no avail. 

Is there something else I should know ? And Yes... of course I'm replacing Alan, with my username...... 

Doug

---

### Post by Sweet Spot on 2007-05-22
Nevermind. I got it installed using this, straight away no hassles:

```

cd ~/Desktop
chmod 755 **filename.run**
sudo ./**filename.run**
```

It did however yield a couple of errors
> Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",


and

> Gtk-CRITICAL **: file gtkentry.c: line 534 (gtk_entry_get_text): assertion `entr y != NULL' failed.

Any ideas on what those mean and what I should do to fix that ?  Thanks. 

doug

---

### Post by hyperair on 2007-05-23
It does look like there's some Gtk problem there. I had similar problems with a game called Shogo, but my problems vanished once I moved from Dapper.

---

