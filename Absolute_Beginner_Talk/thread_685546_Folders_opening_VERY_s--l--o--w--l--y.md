---
title: "Folders opening VERY s--l--o--w--l--y"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Nick8692 on 2008-02-02
I used to run Ubuntu 7.04, and it worked perfectly fine.  Beryl's effects were smooth, and everything opened very quickly.

I recently upgraded to Ubuntu 7.10, and I found that it took about 30 seconds to open folders such as Home.  So I decided to backup my documents, wipe my hard drive, and install fresh.  That worked perfectly. Everything was going great, I had the new Fusion effects running smoothly, and everything responding instantly.  

I then went into add/remove applications and downloaded some programs.  Soon after that, it started taking about 30 seconds to open computer or documents. (or ANY folder :confused:)  Some things open instantly, like synaptic package manager and some other applications, but my documents folder (or any other folder) takes AGES to open.  Its like waiting for paint to dry.  When I click the shutdown icon, that take ages to open as well.  

When I used to open things, my curser briefly changed into the little circle that indicates you computer it is working on your request. when I try to open a folders now, absolutely nothing happens.  Its as if I never clicked it - until the window pops up 30 secs later.

I disabled all the fusion effects and it is still slow, which leads me to believe that it may be a software related problem as it happened after installations - but I’m not quite sure what to do.

Can anyone help me please?

Thanks

---

### Post by philinux on 2008-02-02
Could you post your system specs.

---

### Post by Nick8692 on 2008-02-02
Hi, thanks for your reply.  My specs are:

**CPU**: AMD-K7 Athlon XP 1700+ (1.5 GHz)
**RAM**: 512 MB SDRAM
**GFX**: Abit Siluro GF4 MX-80 (nVidia) 64 MB
Ubuntu is installed on an 80 GB, 7200 RPM hard disk

I think that's all that is relevant, ask if you need anything more.

---

### Post by Nick8692 on 2008-02-02
could it have been something that I installed?

i'm CONFUSED :(

---

### Post by insane_alien on 2008-02-02
can you fire up "top" or the system monitor and see if anything is taking up a huge amount of CPU or RAM? look for high i/o usage as well.

---

### Post by Nick8692 on 2008-02-02
My CPU and memmory are almost idle whilst waiting for documents to load.  I dont think there is any i/o, - at least the light on the front of my pc is idle.  How do you check i/o?

while I was carrying out this experiment, I noted that if I create an empty folder, it loads fine.  Only Home, documents, videos, computer and pictures open slowly, but my videos folder is empty and still takes ages to load. :confused:

I noted that Evolution mail takes almost a minute to load - still with idle memmory..

HELP!

---

### Post by Nick8692 on 2008-02-02
I have an interesting update.  After trying to open several programs and such, only the 'root user' ones will open quickly.  Anything which doesn't require root user access (like, doesn't ask for my password) doesn't open quickly, even though the CPU is practically idle.  It doesn't seem to matter much how big the app is - Mines even takes ages to open.  Synaptic Package Manager, Restricted Drivers Manager and Network are among the ones that open quickly.  Appearance, Screensavers etc won't.

Does this help at all?

EDIT:

And just to support this, using a root terminal I have installed which executes everything in super user mode, entering the command for gnomine (Mines) brings it up quickly.

---

### Post by ed-koala on 2008-02-02
I found something interesting with my setup that you should try.   My Firefox takes 4 seconds to load, not bad, but strangely if I open another Firefox while the first is open, it doesn't take anytime to load, pops right up.  You should try opening two of something like Firefox and see if yours comes up quicker on the second window.

I have no idea why this works this way, maybe another guru can nail down the issue using this info, assuming it works for you like it does me.

---

### Post by Nick8692 on 2008-02-02
> **ed-koala said:**
> I found something interesting with my setup that you should try.   My Firefox takes 4 seconds to load, not bad, but strangely if I open another Firefox while the first is open, it doesn't take anytime to load, pops right up.  You should try opening two of something like Firefox and see if yours comes up quicker on the second window.

I have no idea why this works this way, maybe another guru can nail down the issue using this info, assuming it works for you like it does me.

Firefox is the only app that works like that - pretty clever actually, although why would you need another Firefox when you have tabs?  It does, however, take almost 20 seconds to load - which isn't normal.  But, as I said, only Firefox does this.  Thanks for that info though.

Until a guru comes along...:popcorn:

---

### Post by bruce89 on 2008-02-02
> **Nick8692 said:**
> Firefox is the only app that works like that - pretty clever actually, although why would you need another Firefox when you have tabs?  It does, however, take almost 20 seconds to load - which isn't normal.  But, as I said, only Firefox does this.  Thanks for that info though.:

Hardly. Anything you open in a Linux system (programs, libraries, files) will be cached to RAM. This means if this data is needed again, it can read it from RAM as opposed to the HD. You can see its effect here:
```

bruce@Scooby-Dum:~$ free
             total       used       free     shared    buffers     cached
Mem:       1026312     992080      34232          0      23848     284108
-/+ buffers/cache:     684124     342188
Swap:            0          0          0

```

As you can see, there is very little memory free, but a lot of it (~340MB) is just disk cache.

---

### Post by ed-koala on 2008-02-02
A couple of questions...I'm assuming you have Compiz running from your post.  How many desktop effects do you have enabled?  Do you have effects set to random?  (I do, and compiz just picks one type to perform when opening/closing windows.)  Finally, go to General Options in Compiz and choose the Focus and Raise Behavior tab and see what the time is set to.

Not really sure if that alone is causing you problems, but perhaps you have a lot enabled and it's taxing your video graphics/resources?

I set my Auto Raise Delay down to 5, and it seems to have a slight difference, but then my time wasn't bad to start with.  Can't hurt to check this stuff tho.  :)

---

### Post by Nick8692 on 2008-02-16
no, it cant be this, because I've tried turning off all the effects and it is still slow.  And some things open fast anyway.  Its weird.  Add/ remove programs opens fine, and so does synaptic.  Empty folders open fine, but documents of computer takes the best part of a minute.

It also takes ages to log on as well.

someones GOT to help me......I'm desperate.....:sad: I'm starting to wish i never upgraded...the old Ubuntu worked better.

there's GOT to be a solution

H
E
L
PLEASE!

:confused:

---

### Post by Arthur Archnix on 2008-02-16
You said you added a bunch of programs, which one of those have to do with manging files? For example, did you install a program to monitor and backup your files? Did you install a virus scanner? After thinking about the programs you installed and what they do, to identify your top suspects, then think about unlikely suspects. What programs did you install that probably shouldn't cause this behaviour?

I think your reinstall experiment points strongly at some program interfering with reading files. I'm not sure why it would affect only users, and not root, except that you're doing things in a cli session, so that alone will make it faster. 

Post back with a list of your top, and unlikely suspects, perhaps we'll be able to find a bug report for one, a setting to adjust, or just begin the process of removing them one at a time until we find the culprit.

---

### Post by Krydahl on 2008-02-16
Have a look at etc/hosts

Do you have:

127.0.0.1    localhost   "computername"

Where "computername" is whatever you called your computer not in quotes? If not, try that.

---

### Post by Nick8692 on 2008-02-16
i have the following lines in 'host'

[B]127.0.0.1 localhost
127.0.0.1 nics-desktop.shepherd[/B]

(i called my computer nick.desktop and my surname is Shepherd)

After this there is another 7 lines of stuff

---

### Post by Nick8692 on 2008-02-16
in reply to a previous post inquiring about my installed apps, i post all of my installed applications:

**Accessories**
calculator
character map
dictionary
disk usage annaliser
manage print jobs
take screenshot
text editor
tobermory notes
**Education **
celestia 
celestia space simmulator
stellarium 
easy chem chemical structure editor
little wizzard
childs play
**Games**
AisleRiotSollitaire
blackjack
chess
childsplay
five of more
four in a row
free cell patience
gnometris
lagno
klotski
mahjongg
mines
nibbles
robot
same gnome
souduku
tali
tetravex
**Graphics**
blender 3d modeller (fullscreen)
blender 3d modeller (windowed)
 f - spot photo manager
gimp image gditor
gthumb image viewer
openoffice.org drawing
**internet**
ekiga softphone
evolution mail
firefox web browser
pidgin internet messenger
terminal server client
**office**
evolution
openoffice.orgdatabase
openoffice.org
presentation
openoffice.org
spreadsheet
openoffice.org
wordprocessor
**Sound and video**
acid rip dvd ripper
audacity sound editor
banshee music player
cd player
devede
gnusound
gtick
gtkugitune
hydrogen
movie player
mplayer movie player
recording level monitor
rhythmbox music player
serpentine audio cd creator
sound juicer cd extractor
sound recorder
volume controll
volume moniter
**System tools**
configuration editor
floppy formatter
gdebi packageinstaller
new login
newlogin in a window
root terminal
ubuntu device database

I hope this helps
I really appreciate your concern and help guys

---

### Post by mikeyphi on 2008-02-16
Can't tell from your list...
Try this :Open System/Administration/System Monitor
Under Processes - select (in turn) a process and then click 'end process'
Then check if the action had any effect on your problem

If ending any particular process causes you a system problem - just reboot

---

### Post by Krydahl on 2008-02-16
> **Nick8692 said:**
> i have the following lines in 'host'

[B]127.0.0.1 localhost
127.0.0.1 nics-desktop.shepherd[/B]

(i called my computer nick.desktop and my surname is Shepherd)

After this there is another 7 lines of stuff

Try deleting the .shepherd off the end of nics-desktop.shepherd and see if that helps.

---

### Post by Nick8692 on 2008-02-16
i tried editing the file, but it wont let me save the changes when I'm done

says i don't have the right to do this, but I'm the administrator :confused:

---

### Post by Krydahl on 2008-02-16
```
sudo gedit /etc/hosts
```

---

### Post by Nick8692 on 2008-02-16
i did this, and a text editor opened.....but there was no text...
:confused:

---

### Post by Nick8692 on 2008-02-16
could this be the problem?

---

### Post by vamsibethapudy on 2008-02-16
you said it contained some lines.
how can it be empty?
anyway you can add or edit hosts by left-clicking the network configuration  icon at the top right corner[Default].go to hosts tab
might do the job

---

### Post by Nick8692 on 2008-02-16
i don't know....when i open it with terminal it is empty:confused:

i don't know what you mean by a network configuration icon...

---

### Post by Krydahl on 2008-02-16
/etc/hosts is a file on your computer, it isn't empty because you looked at it earlier.

gedit is a text editor.

sudo is superuser do, this gives you permission to edit the file which is protected because its a system file.

If you got an empty file when you tried this, that is probably because you miss-typed. If you type gedit made_up_name, you'll get an empty file because it doesn't exist. Put some text in and save it and suddenly see that you've created a file.

The network icon should be on your panel by default - I can't remember where because I've deleted mine because I never use it.

You can also get at the same info through the GUI by going system -> administration -> network. Then in the window that pops up, select the hosts tab.

Hope that clarifies things.

---

### Post by Jamoflaw on 2008-02-16
It happened to me after adding myself to my windows workgroup. by deleting the work group reference from my hosts file it made everything load so much faster. I know its not my system (Intel Q6600 with 4gb ram lol)

Jamo

---

### Post by Arthur Archnix on 2008-02-17
It's surprising that you're having trouble finding this, since it was there when you ran that previous command. Try this, and just cut and paste it into the terminal:
```
cd /etc && ls | grep hosts*
```
You should see
```
**hosts**
hosts.allow
hosts.deny
# and maybe this one too
hosts~
```
The one in bold is the one you want to look at and perhaps edit, again, just cut and paste this into your terminal:
```
gksudo gedit /etc/hosts
```
At this point you should have it open with some stuff in it, if not, try opening hosts~. That is, repeat the command above but add ~ to the end of the hosts name. Hopefully you see it now. If you have trouble following the instructions given above post back here with the output of this command, and someone can provide you with more detailed instructions. I haven't yet got through any of your programs, because this hosts thing seems to be an easier and more likely fix.
```
cat /etc/hosts
```
Here, just for example, is what my hosts file looks like:
> 127.0.0.1       localhost
127.0.1.1       archnix

# The following lines are desirable for IPv6 capable hosts
# ::1     ip6-localhost ip6-loopback
# fe00::0 ip6-localnet
# ff00::0 ip6-mcastprefix
# ff02::1 ip6-allnodes
# ff02::2 ip6-allrouters
# ff02::3 ip6-allhosts


---

### Post by Nick8692 on 2008-02-17
YEAH!!! it WORKED :)
Thanks so much guys!

All i had to do was delete the .shepherd off the end and it worked! 

thanks!

---

