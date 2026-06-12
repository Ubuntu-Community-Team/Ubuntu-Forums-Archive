---
title: "Opening a Txt file"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-11-10
Hi,  I just installed 7.10 on another drive that I can boot to from a USB external
drive.  Everything is pretty much working great except this small thing that scares
me..... Well, I made a text file full of Cut and Pastes I did to help me remember
some things in ubuntu such as how to put the trash can on the desk top, how
to temporary use Nautilus as a super user, ect ect.... basically just a bunch
of help me's I put together in a txt file...... Well, I put all these on my thumb
drive so I could read them when I booted up my Ubuntu.....

Here is what scares me.... Everytime I try to open any txt file that I made
this message is displayed.  Is this something I should worry about? Txt file
being an exe?

[IMG]http://img403.imageshack.us/img403/9665/myscreenshotte3.png[/IMG]

If I choose run, it wants me to enter my admin password.
If I choose display, it opens and I can read it..... 
Is this normal? I created a txt file myself on the new Ubuntu
and it doesn't do that.  Could it be because I copied it over
and it needs some type of permission because I don't own the file or something?

---

### Post by matthewcraig on 2007-11-10
The permissions are funny.  Run a "chmod 644 *.txt" on them.

---

### Post by enderwig on 2007-11-10
It is normal, just click display to read it.

---

### Post by Scunizi on 2007-11-10
Just a suggestion.  Instead of keeping your notes in a text file, check out synaptic for VYM.  It's what I've been using for the last three versions of Ubuntu and works great.  It's a mindmapping tool that is very intuitive. hint... add notes to a box by hitting ctrl+e.  

I've kept track of how to install a pdf print driver, programs that I have an interest in but not installed, Apache server stuff.. Just about anything.. including the packing list for camping.

---

### Post by catfacts on 2007-11-10
You see in windows everything is executable, where as in linux only things that need to are. It sees executable as a security flaw, which it is as this is how windows is so buggy. For a gui right click the file and go to permissions tab and unclick allow execution. This is normal when importing windows files. You will notice that linux holds to standards more riggorously. I have noticed that in .php files if there are not <?php ?> tags it says, this is a php file but only contains html, this may be a security breach. This is nice thou because it autodetects file types, say you have image and in windows you would need to rename to file.jpg file.png file.gif to see what kind of file it is, where linux will open it correctally. You will notice quirks like this in linux for a few months then you will have them down pretty good :)

---

### Post by FuturePilot on 2007-11-10
That's just part of Nautilus. You can change that behavior by opening a Nautilus window and going Edit>Preferences. Go to the Behavior tab and there's a section for Executable Text Files. You can change the way Nautilus handles text files.

---

### Post by Paul820 on 2007-11-10
If you open your home folder the go to edit->Preferences->Behaviour there is an option to **view executable text files when they are opened**, check the box and it won't ask you again for txt files.
EDIT: What FuturePilot said, lol

---

### Post by Orbital75 on 2007-11-10
Thanks guys, I was worried there for a minute. I'm not use to Linux yet so when I saw
that pop up it scared me a little.  I know in Windows Virus authors sometimes give their
viruses double extensions and most people don't have the show extensions feature
tuned on. So I was thinking that file could have been altered by something on my Win Machine
and Ubuntu recognized it as something different and wanted to ask permission to run it. 
Knowing a Windows machine would have just let it run....
Of course I'm a pretty safe windows user so I would be shocked if I had been compromised.
I run myself as a Limited User as well as run NOD32, Spybot, AdAware, Defender, along with a personal
firewall and a NAT Router. I also have common sense not to do stupid things so I would have been
really shocked if I had been infected......

Sounds like Linux is smart about extensions and knows how to open things without having to rely on extensions. 
I really like the Linux platform and not having to worry about running all those memory hog programs to protect
my machine.... It's just nice to know.  Not only is Windows a target for Malware and Viruses it's also Expensive
So I'm hoping to be along for the Linux ride for a long time.  

Thanks again everyone for the help.

---

### Post by mivo on 2007-11-10
> **Scunizi said:**
> Just a suggestion.  Instead of keeping your notes in a text file, check out synaptic for VYM. 

Is there a repository with the current version? The one in Gutsy's multiverse is 14 months older than the most recent stable version at VYM's project page. No debs there, just source, rpms and a Mac archive.

---

### Post by Orbital75 on 2007-11-10
I may just give that a try......  Sounds like a pretty nice program.

---

