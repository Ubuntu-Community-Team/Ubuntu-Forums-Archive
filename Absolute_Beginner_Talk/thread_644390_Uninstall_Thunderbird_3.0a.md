---
title: "Uninstall Thunderbird 3.0a?"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by tzd on 2007-12-18
Hi everyone!

I was unable to find a previous post regarding this version of thunderbird.
About a week ago I was running windows with thunderbird+lightning ext.
I decided to switch to ubuntu (now kubuntu) and everything worked perfectly until I've tried adding thunderbird 2.0.0.9 (think that's the latest official rel.) combined with lightning ext. 0.7 which didn't work at all. 

I then thought I've used version 3.0 of thunderbird and that must have been the reason why it didn't work on linux with version 2.0.0.9.
Foolish of me of course not checking forums before :( 

 I've tried delete it (build 3.0a) by uninstalling packages as well as removing two folders in my home directory ".thunderbird" and also ".mozilla-thunderbird". I then reinstalled version 2.0.0.9 by using the command: 

sudo apt-get install thunderbird

I have also tried installing v. 2.0.0.9 via official mozilla site but EVERY time I try to run my mail program it continues to load version 3.0a instead of version 2.0.0.9. 

Can someone please help me uninstall version 3.0? 
I am 1 week old in the Linuxworld but im slowly learning :)

Thanks in advance!

/Johan

---

### Post by wolfvorkian1 on 2007-12-18
> **tzd said:**
> Hi everyone!

I
Can someone please help me uninstall version 3.0? 
I am 1 week old in the Linuxworld but im slowly learning :)

Thanks in advance!

/Johan

One approach you might use is to download the search program called 'slocate' I believe it is called. After it is installed I believe you have to build a database, I don't remember if it does it by default or if you have to do it yourself.

```
sudo updatedb
```

Then do a search for thunderbird. 

```
locate thunderbird
```

This should help you find the files to delete that are messing with you. As you have probably guessed, uninstalling a application with apt-get or synaptic doesn't always get rid of all the files. 

Locate is a good tool, seems to be much better than the 'find' function in Nautilus.

---

### Post by nowshining on 2007-12-18
it's already installed i think in gutsy

it autoupdates i think

i could be wrong

yes the code to update is right...update it often tho. :) as it can show outdated entries when they are not there..

oh and u'll have to enter the commands in applicaitons - accessories -- terminal

when u input sudo itta ask u for ur password

DO NOT worry if u don't see anything as u type, this is normal and for security reasons, just type it out as usual and then hit the enter key.

---

### Post by tzd on 2007-12-19
> **wolfvorkian1 said:**
> 

```
sudo updatedb
```

Then do a search for thunderbird. 

```
locate thunderbird
```

This should help you find the files to delete that are messing with you. As you have probably guessed, uninstalling a application with apt-get or synaptic doesn't always get rid of all the files. 

Locate is a good tool, seems to be much better than the 'find' function in Nautilus.

Thanks for your replies guys!!

I've located all these files by using "locate thunderbird" and also "locate thunderbird*".
I then removed every single entry until there were no thunderbird entries left.
I then restarted my computer and installed thunderbird v2.0.0.8 via Konsole
 (sudo apt-get install thunderbird).

The program was downloaded and installed. When i try to start it via K-menu it won't start. I am able to click the icon but that's it. 

Which files do I need or what do I need to type to get this bird running?

---

### Post by nowshining on 2007-12-19
try this

open up the terminal again and type

thunderbird

post the output if any from the terminal

---

### Post by tzd on 2007-12-19
ok this is the output I received (I'll translate it from Swedish to English further down):

-----------------------------------------------------------
johan@Penguin:~$ thunderbird
Programmet "thunderbird" är för närvarande inte installerat.  Du kan installera det genom att ange:
sudo apt-get install thunderbird
bash: thunderbird: kommandot hittades inte
johan@Penguin:~$ sudo apt-get install thunderbird
[sudo] password for johan:
Läser paketlistor... Färdig
Bygger beroendeträd
Läser tillståndsinformation... Färdig
thunderbird är redan den senaste versionen.
Följande paket har installerats automatiskt och är inte längre nödvändiga:
  gnome-keyring libstdc++5 libgtop2-common libgnome-keyring0 gdebi
  libnotify-bin python-glade2 python-vte libvte9 libglade2-0 libgtop2-7 gksu
  gnome-icon-theme libgksu2-0 gcc-3.3-base libvte-common
Använd "apt-get autoremove" för att ta bort dem.
0 uppgraderade, 0 nyinstallerade, 0 att ta bort och 0 ej uppgraderade.
johan@Penguin:~$ thunderbird
Programmet "thunderbird" är för närvarande inte installerat.  Du kan installera det genom att ange:
sudo apt-get install thunderbird
bash: thunderbird: kommandot hittades inte
--------------------------------------------------------------------------
The first sentences tells me the program "Thunderbird" is currently not installed. It continues and tells me to use the command: sudo apt-get install thunderbird 
to install the program.

I then do this. After running this command i receive a message saying that I already have the latest version of thuderbird. 
Nothing is being downloaded or upgraded/installed either when running the install command. 

I also used the command sudo updatedb between and after above commands.

Please tell me that helps you?
Just to make sure nothing actually changed after typing both "thunderbird" and then "installing" it again via sudo apt-get install .... I tried once again typing thunderbird and received the same error telling me to install thunderbird.

---

### Post by wolfvorkian1 on 2007-12-19
> **tzd said:**
> ok this is the output I received (I'll translate it from Swedish to English further down):


Please tell me that helps you?
Just to make sure nothing actually changed after typing both "thunderbird" and then "installing" it again via sudo apt-get install .... I tried once again typing thunderbird and received the same error telling me to install thunderbird.

Ubuntu saves all the programs it installs after the original installation in /var/cache/apt/archives, perhaps this is messing things up.

Try this  in terminal. It will delete all the files in that directory and force apt-get to go on line and bring in a fresh application, otherwise it will install from your hard drive first. Don't worry, you are not deleting installed applications. 

```
sudo apt-get clean
```Then type thunderbird again in your terminal and see what it says. Then do what it says and if that doesn't work, post again.

---

### Post by tzd on 2007-12-19
Ok, after using the : 

```
sudo apt-get clean
```

it then asks me to install thunderbird as mentioned before via :
 
```
sudo apt-get install thunderbird
```

the package download works and installs thunderbird: 2.0.0.8~pre071022+nobinonly-0ubuntu0.7.10

I then type: thunderbird
and we're back to where we started unfortunately. The message i receive is:

----------------------------------------------------------------------
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
johan@Penguin:~$ sudo updatedb
johan@Penguin:~$ thunderbird
Programmet "thunderbird" är för närvarande inte installerat.  Du kan installera det genom att ange:
sudo apt-get install thunderbird
bash: thunderbird: kommandot hittades inte
johan@Penguin:~$ sudo apt-get clean
johan@Penguin:~$ thunderbird
Programmet "thunderbird" är för närvarande inte installerat.  Du kan installera det genom att ange:
sudo apt-get install thunderbird
bash: thunderbird: kommandot hittades inte
--------------------------------------------------

I included the last two sentences :
(Processing triggers for libc6 ...ldconfig deferred processing now taking place)
 from the install command in case that tells you anything? 

The end message says: bash: thunderbird: the command couldn't be found


In the first run when i deleted all thunderbird entries I only had 2 entries relating to thunderbird left and those 2 entries were custom icons. I logged in as root and deleted the various thunderbird entries. Thought I'd make that more clear since my foolishness by doing all this was probably the thing that put me here in the first place :/

Are there any default thunderbird files included in Kubuntu distribution? 
Perhaps i need to restore these if there are files like that?

---

### Post by wolfvorkian1 on 2007-12-19
I don't use Thunderbird but the command to run the program is not just "thunderbird" I found out but 

```
mozilla-thunderbird
```

See if this helps. Run the above in terminal and see if the elusive bird appears.;-)

---

### Post by tzd on 2007-12-20
johan@Penguin:~$ mozilla-thunderbird
bash: mozilla-thunderbird: the command couldn't be found

thunderbird is installed, yet it won't find the executable file. When i try running it via "alt+F2" and typing "thunderbird" i get the mesage:

KDEInit could not start "thunderbird".:
Could not find 'thunderbird' executable.

and when i type "mozilla-thunderbird" in the "alt+F2" window i get:
mozilla-thunderbird
Could not run the given command.

I think i need to associate the programs executable file with the command by editing a path or something if that's possible?

---

### Post by nowshining on 2007-12-20
okay try these

sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get check


Below u will find apt-gets commands (what u can put after apt-get) & what they do

  update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   purge - Remove and purge packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies


then try re-installing and running it again

---

### Post by tzd on 2007-12-20
> **nowshining said:**
> okay try these

sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get check

then try re-installing and running it again

Ok I've tried the above commands, I then ran the purge command to remove thunderbird. Ran the above 3 commands once again. Reinstalled Thunderbird via install command.
Ran the 3 above commands and then tried running thunderbird with:

thunderbird
mozilla-thunderbird

the output is the same as before. It can't find the command when trying with "mozilla-thunderbird" and when trying with just "thunderbird" i get the message that thunderbird isn't installed and that i can install it via sudo apt-get install...

This seems to be doomed unfortunately... I'm thinking of reinstalling the whole OS to get it straight.
Not much harm done since I've only had it for about a week. 
Just wondering for future references, are there any backup/restore options in ubuntu/kubuntu just in case something like this ever happen again?

I'll wait a few more hours with the reinstall just in case one of you helpful guys comes up with something that'll save me :)


Thank you both very much for your time and help in this matter!

---

### Post by nowshining on 2007-12-20
ah no need to re-install if u did not do it that much.... however since ur having problems redo those commands but do not try another re-install from the synaptic package manager, and from here on u'll do it by an script file and try the one from the main website (not the ubuntu modified version)

in other words, it's probably the softwares faults - the apps fault.. 


also this gives a bit of background on ubuntu and software packages not being added as new for stable releases of the os.

[http://ubuntuzilla.wiki.sourceforge.net/?token=4b8f5dee886426928bfd7d43d2217f65](http://ubuntuzilla.wiki.sourceforge.net/?token=4b8f5dee886426928bfd7d43d2217f65)

---

### Post by tzd on 2007-12-20
I've tried that script as well before but, just as the last time i used it, it "hangs" during install.
I am unable to receive a public key or something.

Unable to retrieve Mozilla Software Releases Public key from pgp.mit.edu . Trying again...
gpg: failed to create temporary file `/home/johan/.gnupg/.#lk0x811d2c8.Penguin.10056': Åtkomst nekas
gpg: nyckelblockresurs "/home/johan/.gnupg/secring.gpg": allmänt fel
gpg: failed to create temporary file `/home/johan/.gnupg/.#lk0x81202e0.Penguin.10056': Åtkomst nekas
gpg: nyckelblockresurs "/home/johan/.gnupg/pubring.gpg": allmänt fel
gpg: begär nyckeln 0E3606D9 från hkp-servern wwwkeys.pgp.net
gpg: begär nyckeln 812347DD från hkp-servern wwwkeys.pgp.net
gpg: hittade ingen nyckelring som gick att skriva till: eof
gpg: fel vid läsning av "[stream]": allmänt fel



It keeps trying to receive this key from various places but it won't work.
It says something about: couldn't find a writeable keyring

---

### Post by Andre_3608 on 2007-12-20
Would it not be easiest simply to use System / Administration / Synaptic Package Manager, type in Thunderbird, mark it for installation, apply and off you go?  Admittedly, I'm no tyro!  Good luck...

---

### Post by tzd on 2007-12-20
Tried that already Andre.... think that was among the first things i did ;)
Thanks for your help though!

Was on irc before and managed to solve the whole issue... at least to an acceptable point :)
The thing we did to solve the issue wsa to go into thunderbirds program folder located at:

/usr/lib/thunderbird

we then double clicked the file named "thunderbird" that was in the mentioned directory.
The program then started up as normal (version 2.0.0.6 though).
I closed the program and wanted to try to run it via K-menu. That didn't work.
To make it work from K-menu as well I had to check the properties for the k-menu link and from there link it to the actual program file "thunderbird" in /usr/lib/thunderbird/
After that the program starts up just as it should. Only thing now was that I had to change the working folder as well to where my mail config were (this was blank originally in the Kmenu). So now it works like a charm :)

The only thing that still doesn't work is when i try running it via konsole. I still get those previous error messages saying that the software isnt installed etc.
The guy i spoke to on irc thought it might have to do with the packages for the nightly version (3.0a).

Anyhow, i'm now a very happy and lucky man! :)

Thank you all for your help and efforts on this matter!!!

---

### Post by nowshining on 2007-12-20
i'm happy u got it selved. :) and u did a symbolic link if i remember correctly...

---

