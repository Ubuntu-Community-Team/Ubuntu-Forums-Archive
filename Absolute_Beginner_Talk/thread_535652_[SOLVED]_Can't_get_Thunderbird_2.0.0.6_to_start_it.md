---
title: "[SOLVED] Can't get Thunderbird 2.0.0.6 to start its install (in Feisty)"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-08-26
I want to install Thunderbird 2.0.0.6 in my Ubuntu Feisty laptop. I went to the Thunderbird home page and downloaded it. Once downloaded, I extracted the files. That gave me a folder on my desktop labelled "Thunderbird". But when I right-click on that, I was expecting to find an option for the "installer" or the "unpackager". But no such option is there. What do I have to do to install Thunderbird 2.0.0.6?

I could go through Ubuntu's Add-Remove programs application, but the version of Thunderbird available there is only 1.5.0.1.3 or something like that. I need the latest one-- the 2.0.0.6 which is available on the TB homepage. How can I get it to load?

---

### Post by Majorix on 2007-08-26
Why do you need the latest version? On my feisty install Thunderbird 1.5 worked just fine. If you want all the latest software come to Gutsy and enable the backports. Its your choice.

---

### Post by swarup on 2007-08-26
> **Majorix said:**
> Why do you need the latest version? On my feisty install Thunderbird 1.5 worked just fine. If you want all the latest software come to Gutsy and enable the backports. Its your choice.

I need version TB 2.0 because there is an add-on which I critically need, and it requires 2.0 or later.

The add-on is called XNote, and the link to it is here:

[https://addons.mozilla.org/en-US/thunderbird/addon/3093](https://addons.mozilla.org/en-US/thunderbird/addon/3093)

Anyhow, I should be able to install TB 2.0. I installed TB 2.0 on my desktop computer (Ubuntu Feisty) and it loaded without a hitch. Gave me the installer icon right on the desktop. I clicked on it, and it installed right away. I don't know why it isn't doing that on my laptop. There must be a Debian Unpackager or something that will know what to do with this "TB Folder". But no such unpackager appears when I right-click on the folder.

---

### Post by Majorix on 2007-08-26
Can you tell me the name of the file you have there? Also, if you extracted it somehow, can you send the result of ls? Thanks.

---

### Post by flatwombat on 2007-08-26
There should be a file simply saying 'thunderbird' which will launch it.  No installer necessary as I recall.  (Edit:  yes, just downloaded and launched it - still just as easy)

---

### Post by swarup on 2007-08-26
> **Majorix said:**
> Can you tell me the name of the file you have there? Also, if you extracted it somehow, can you send the result of ls? Thanks.

The folder is just called "thunderbird". First I downloaded  2.0.0.6 from the TB homepage, and it gave me a package which required extraction. I gave the order to "extract files", and the result was the folder on my desktop called "thunderbird". If there is a terminal command you want me to do with this folder ie "ls", please give the exact command in terminal. I do not know how to make the ls command refer to this "thunderbird" folder.

==> I just got "ls" to work with the "thunderbird folder. Here below is the output:


swarup@swarup-laptop:~$ ls /home/swarup/Desktop/thunderbird
chrome              libfreebl3.so    libsoftokn3.so          removed-files
components          libldap50.so     libssl3.so              res
defaults            libmozjs.so      libxpcom_compat.so      run-mozilla.sh
dependentlibs.list  libnspr4.so      libxpcom_core.so        thunderbird
dictionaries        libnss3.so       libxpcom.so             thunderbird-bin
extensions          libnssckbi.so    libxpistub.so           updater
greprefs            libplc4.so       license.html            updater.ini
icons               libplds4.so      LICENSE.txt             updates
init.d              libprldap50.so   mozilla-installer-bin   xpicleanup
isp                 libsmime3.so     mozilla-xremote-client
libfreebl3.chk      libsoftokn3.chk  README.txt

---

### Post by por100pre1 on 2007-08-26
Use [Ubuntuzilla]("http://ubuntuzilla.wiki.sourceforge.net/") to install Thunderbird 2. You won't go wrong.

---

### Post by Majorix on 2007-08-26
Ok sorry I sometimes lose myself and forget that I am posting in the beginner forums.

I am now downloading that file and will tell you how to install it in just a moment.

EDIT: Running the file called "thunderbird" should do the trick. If not write back.

---

### Post by John.Michael.Kane on 2007-08-26
> **por100pre1 said:**
> Use [Ubuntuzilla]("http://ubuntuzilla.wiki.sourceforge.net/") to install Thunderbird 2. You won't go wrong.

That is one method. Below is another.
[Thunderbird 2 feisty backport]("http://ubuntu.iuculano.it/dists/feisty/thunderbird/")

---

### Post by swarup on 2007-08-26
> **por100pre1 said:**
> Use [Ubuntuzilla]("http://ubuntuzilla.wiki.sourceforge.net/") to install Thunderbird 2. You won't go wrong.

I went to this site and followed the directions perfectly. First I downloaded the Ubuntuzilla downloader, and installed that. Then I went to a terminal window and typed the line they gave for installing Thunderbird. Everything seemed to go fine, and Thunderbird installed. But now, when I go to Applications -> Internet -> Thunderbird and click to open TB, it looks like it is trying to open something, but after around 20 seconds of trying, it just gives up and nothing opens. So what happened? Did I get a messed up version of the program somehow? I guess I'll have to uninstall it and try doing it some other way?

---

### Post by Majorix on 2007-08-26
And why did you give up with the first way? That was the reason you opened this topic...

---

### Post by por100pre1 on 2007-08-26
> **swarup said:**
> I went to this site and followed the directions perfectly. First I downloaded the Ubuntuzilla downloader, and installed that. Then I went to a terminal window and typed the line they gave for installing Thunderbird. Everything seemed to go fine, and Thunderbird installed. But now, when I go to Applications -> Internet -> Thunderbird and click to open TB, it looks like it is trying to open something, but after around 20 seconds of trying, it just gives up and nothing opens. So what happened? Did I get a messed up version of the program somehow? I guess I'll have to uninstall it and try doing it some other way?

Try opening Thunderbird using a command interminal windows to see what's going on:

```
thunderbird
```

Verify the command in the launcher, it must be just thunderbird, not mozilla-thunderbird.

---

### Post by flatwombat on 2007-08-26
If you download Thunderbird and move it to your /home/username; then go to the .tar.gz and right-click on it, you'll have the option to 'extract here'.  Okay, then it will produce a folder named "thunderbird".  Open it and you'll find an icon inside simply saying "thunderbird".  Click on that icon and it will launch your mail program.  You can then add a launcher to the desktop if you wish.

---

### Post by swarup on 2007-08-26
> **flatwombat said:**
> If you download Thunderbird and move it to your /home/username; then go to the .tar.gz and right-click on it, you'll have the option to 'extract here'.  Okay, then it will produce a folder named "thunderbird".  Open it and you'll find an icon inside simply saying "thunderbird".  Click on that icon and it will launch your mail program.  You can then add a launcher to the desktop if you wish.

I had downloaded it to the desktop. Then I had extracted it, as you describe above. Then it produced a folder named "thunderbird". There is indeed an icon inside it saying "thunderbird". I clicked on it, and it asked me if I wanted to run it. It said ""thunderbird" is an executable text file". I clicked on run, and the computer made a little noise like it was going to do something, but nothing happened. That "Thunderbird" icon when one right clicks and checks properties, says it is a "shell script". Is that the one? It does not seem to be working. I do not know why.

---

### Post by swarup on 2007-08-26
> **Majorix said:**
> And why did you give up with the first way? That was the reason you opened this topic...

I didn't give up. But it didn't seem to be working. That is why I started trying other ways. 

So I tried via the Ubuntuzilla link which por100pre1 suggested. Everything went smoothly, but in the end I couldn't get TB to launch. So I deleted it. Now I do not have any version of TB in the computer. I have again downloaded the .tar.gz  file. I will again try extracting from there and then clicking on the Thunderbird file to install. But that doesn't seem to be working either.

I tried clicking on the icon called "thunderbird", and running it. Nothing happens. I tried the option to "run in terminal". It starts to open a terminal window, but then shuts before the terminal windows actually shows up. For some reason, this thing is just not working.

---

### Post by swarup on 2007-08-26
> **por100pre1 said:**
> Try opening Thunderbird using a command interminal windows to see what's going on:

```
thunderbird
```

Verify the command in the launcher, it must be just thunderbird, not mozilla-thunderbird.

I had deleted this version after it didn't work. Now again I reloaded it. Again it loaded quite smoothly, with the TB launcher appearing in Applications -> Internet. I clicked on it and tried to launch TB. Again nothing happened. 

As you have suggested above, I opened a terminal window and typed in "thunderbird". Nothing at all happens. 

swarup@swarup-laptop:~$ thunderbird
swarup@swarup-laptop:~$ thunderbird
swarup@swarup-laptop:~$ 


I put a launcher icon on the desktop and verified its launch command. It had "mozilla-thunderbird" there. So as you instructed, I made it just "thunderbird". Still, it is not working. 

So what should I do now?

---

### Post by Majorix on 2007-08-26
Add the thunderbird repo. Someone posted it on the prev page.

---

### Post by swarup on 2007-08-26
> **Majorix said:**
> Add the thunderbird repo. Someone posted it on the prev page.

Could you tell me a little more clearly what you want me to do? I do not understand what "Add the thunderbird repo" means. Do you want me to uninstall what I currently have and load something in its place? Or keep what I have, and add something in addition? If so, what exactly do you want me to add? Who posted the thunderbird repo on the previous page? And where should I put it when I find it?

---

### Post by flatwombat on 2007-08-26
Agreed on the repo.  Something's missing in the system that prevents Tbird from loading properly as downloaded and since you're getting no feedback from the terminal on errors, there's little to check.  Dang!  I should boot into Mint and see what's installed there; it's Ubuntu (kinda) based after all.

---

### Post by Majorix on 2007-08-26
> **SD-Plissken said:**
> That is one method. Below is another.
[Thunderbird 2 feisty backport]("http://ubuntu.iuculano.it/dists/feisty/thunderbird/")

This is the one I am talking about. There are instructions on that link on how to add the repo. Btw a repo is like a depot on internet containing software.

And I would suggest you get rid of all those you have at hand since they don't work. No need to keep them I think?

And finally please don't ask so many questions at once haha I get confused :D

---

### Post by swarup on 2007-08-26
> **Majorix said:**
> This is the one I am talking about. There are instructions on that link on how to add the repo. Btw a repo is like a depot on internet containing software.

 :D

I had gone to that site earlier, but gave it up when I saw that the instructions were technical. They should make the instructions in clear English for those who are new to this. Here below is all they gave. Could you give me the actual lines I need to put in terminal, because I cannot follow what they have given below:

> 
 You can use apt to download and install the packages. Use the following lines in /etc/apt/sources.list and use the command sudo apt-get update to enable downloading from this component.

Don't forget to read the notice on the frontpage!
```
deb http://ubuntu.iuculano.it feisty thunderbird
deb-src http://ubuntu.iuculano.it feisty thunderbird 
```

Also: There are so many packages on that repo page, I don't know am I supposed to somehow get ALL the things on that page? Including "enigmail", "thunderbird", and "thunderbird locales"?


> **Majorix said:**
> And I would suggest you get rid of all those you have at hand since they don't work. No need to keep them I think? :D

What about the version I have currently installed from Ubuntuzilla? Do you mean I should uninstall that? Or, is what I am adding from the repo going to somehow work together with the existing Ubuntuzilla install to make it complete (meaning in that case I should keep the Ubuntuzilla install)?

---

### Post by Majorix on 2007-08-26
Add the key to your database like this:
```
wget http://ubuntu.iuculano.it/AE3BE9AA.gpg -O- | sudo apt-key add -
```

Then you will have to edit your sources.list as follows:
```
sudo gedit /etc/apt/sources.list
```

Add those lines mentioned on that site, I mean these:
> deb [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty thunderbird
deb-src [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty thunderbird

Update and install:
```
sudo apt-get update && sudo apt-get install thunderbird
```

---

### Post by flatwombat on 2007-08-26
I'm not in Feisty at the moment, but I'll speak to you about the CLI instructions you've got there.  Simply open a terminal and type:
> 
sudo gedit /etc/apt/sources.list 
give your password and a new window will open with your existing repositories.  Then, copy & paste the lines in at the bottom of your list:
> 
deb [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty thunderbird
deb-src [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty thunderbird

Then 'save' and close that window and then type:
> 
sudo apt-get update

Now, with the new repository installed, it will see that the Thunderbird in luculano.it is an upgrade to your existing Thunderbird and will handle the dependency issues and upgrade.

**OOPS!  Sorry for posting over you Marjorix!  (Do what he said... 'cause we agree)**

Of course...all that is subject to what you've already done with that other set of instructions.  I haven't checked them and can't say if you've already done an proper update or not.  If Thunderbird is updated, then the new update won't find anything to do.

---

### Post by swarup on 2007-08-26
Many thanks to both of you. I'm going to go ahead now and put in terminal the lines Marjorix outlines. It should only take 5 minutes. I'll let you know what happened. 

So as I understand, this will all be done keeping the version of 2.0.0.6 I got from Ubuntuzilla installed. I'll let you know what happened in 5 minutes.

---

### Post by r_l on 2007-08-26
> **swarup said:**
> I want to install Thunderbird 2.0.0.6 in my Ubuntu Feisty laptop. I went to the Thunderbird home page and downloaded it. Once downloaded, I extracted the files. That gave me a folder on my desktop labelled "Thunderbird". But when I right-click on that, I was expecting to find an option for the "installer" or the "unpackager". But no such option is there. What do I have to do to install Thunderbird 2.0.0.6?

I could go through Ubuntu's Add-Remove programs application, but the version of Thunderbird available there is only 1.5.0.1.3 or something like that. I need the latest one-- the 2.0.0.6 which is available on the TB homepage. How can I get it to load?

If you like you could try Ubuntuzilla.  You can use it to install the latest Tbird and FFox for you.

[URL="http://ubuntuzilla.wiki.sourceforge.net/"]http://ubuntuzilla.wiki.sourceforge.net/
[/URL]

I used it to install Tbird2 and it worked like a charm for me.

RL

---

### Post by swarup on 2007-08-26
I don't think that everything happened that was supposed to happen. (please see last line of this post. I later realized my error.) Here below is the terminal output. Sometimes the screen did not return to a normal cursor line, and I didn't know what to do. So I moved ahead and pasted in the next line, but I'm not sure whether it all registered properly.

```
swarup@swarup-laptop:~$ wget http://ubuntu.iuculano.it/AE3BE9AA.gpg -O- | sudo apt-key add -
--23:23:36--  http://ubuntu.iuculano.it/AE3BE9AA.gpg
           => `-'
Resolving ubuntu.iuculano.it... Password:89.163.146.211
Connecting to ubuntu.iuculano.it|89.163.146.211|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,210 (2.2K) [application/pgp-keys]

100%[====================================>] 2,210         --.--K/s             

23:23:37 (351.62 KB/s) - `-' saved [2210/2210]


Sorry, try again.
Password:
OK
swarup@swarup-laptop:~$ sudo gedit /etc/apt/sources.list
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
GTK Panel of SCIM 1.4.4


deb http://ubuntu.iuculano.it feisty thunderbird
^?
deb-src http://ubuntu.iuculano.it feisty thunderbird
sudo apt-get update && sudo apt-get install thunderbird
```

I think some of the lines need to be repeated again, don't they?

==> I see my error now. I was supposed to put those two lines into the sources.list file that opened. I'll do that now, and then try again to move ahead from there according to your directions.

---

### Post by swarup on 2007-08-26
Ok. I think I was able to follow everything you both said to do. I pasted those two lines into the sources file, and saved and closed it. Then I did the 

"sudo apt-get update && sudo apt-get install thunderbird"

It seemed to install a bunch of stuff after that. 

But the end result is that TB still does not start up. It makes an effort to, but nothing ever comes up on the screen.

Anyhow, here below is the output from the terminal screen for what I did. It picks up from where the last terminal window I sent you, left off.:

```
swarup@swarup-laptop:~$ sudo apt-get update && sudo apt-get install thunderbird
Password:
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US                         
Get:1 http://ubuntu.iuculano.it feisty Release.gpg [189B]                                                                   
Ign http://ubuntu.iuculano.it feisty/thunderbird Translation-en_US                                                          
Get:2 http://security.ubuntu.com feisty-security Release.gpg [191B]                                                         
Ign http://security.ubuntu.com feisty-security/main Translation-en_US                                                       
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US                                                 
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US                                                   
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US                                                 
Get:3 http://medibuntu.sos-sts.com feisty Release.gpg [189B]                                                                
Ign http://medibuntu.sos-sts.com feisty/free Translation-en_US                                                              
Ign http://medibuntu.sos-sts.com feisty/non-free Translation-en_US                                                          
Get:4 http://www.getautomatix.com feisty Release.gpg [189B]                                                                 
Get:5 http://archive.canonical.com feisty-commercial Release.gpg [191B]                                                     
Ign http://www.getautomatix.com feisty/main Translation-en_US                                                               
Get:6 http://archive.ubuntu.com feisty-backports Release.gpg [191B]                                                         
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_US                                                       
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_US                                                 
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_US                                                   
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_US                                                 
Get:7 http://archive.ubuntu.com feisty-updates Release.gpg [191B]                                                           
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_US                                                     
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_US                                                   
Get:8 http://archive.ubuntu.com feisty-security Release.gpg [191B]                                                          
Get:9 http://us.archive.ubuntu.com feisty Release.gpg [191B]                                                                
Ign http://archive.ubuntu.com feisty-security/main Translation-en_US                                                        
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                                                              
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US                                                        
Ign http://archive.canonical.com feisty-commercial/main Translation-en_US                                                   
Get:10 http://ubuntu.iuculano.it feisty Release [13.9kB]                                                                    
Hit http://security.ubuntu.com feisty-security Release                                                                      
Err http://wine.lowvoice.nl feisty Release.gpg                                                                              
  Could not resolve 'wine.lowvoice.nl'
Hit http://medibuntu.sos-sts.com feisty Release                                                                             
Hit http://www.getautomatix.com feisty Release                                                                              
Hit http://archive.canonical.com feisty-commercial Release                                                                  
Ign http://archive.ubuntu.com feisty-security/restricted Translation-en_US                                                  
Ign http://archive.ubuntu.com feisty-security/universe Translation-en_US                                                    
Ign http://archive.ubuntu.com feisty-security/multiverse Translation-en_US                                                  
Hit http://archive.ubuntu.com feisty-backports Release                                                                      
Hit http://archive.ubuntu.com feisty-updates Release                                                                        
Hit http://archive.ubuntu.com feisty-security Release                                                                       
Err http://wine.lowvoice.nl feisty/main Translation-en_US                       
  Could not resolve 'wine.lowvoice.nl'
Hit http://security.ubuntu.com feisty-security/main Packages                                                                
Ign http://medibuntu.sos-sts.com feisty/free Packages                                                                       
Hit http://www.getautomatix.com feisty/main Packages                                                                        
Ign http://wine.lowvoice.nl feisty Release                                                                                  
Hit http://archive.canonical.com feisty-commercial/main Packages                                                            
Hit http://security.ubuntu.com feisty-security/restricted Packages                                                         
Hit http://security.ubuntu.com feisty-security/main Sources                                                                
Hit http://security.ubuntu.com feisty-security/restricted Sources                                                          
Hit http://security.ubuntu.com feisty-security/universe Packages                                                           
Hit http://security.ubuntu.com feisty-security/universe Sources                                                            
Ign http://medibuntu.sos-sts.com feisty/non-free Packages                                                                  
Ign http://medibuntu.sos-sts.com feisty/free Sources                                                                       
Hit http://security.ubuntu.com feisty-security/multiverse Packages                                                         
Hit http://security.ubuntu.com feisty-security/multiverse Sources                                                          
Ign http://medibuntu.sos-sts.com feisty/non-free Sources                                                                   
Hit http://medibuntu.sos-sts.com feisty/free Packages                                                                      
Ign http://wine.lowvoice.nl feisty/main Packages                                                     
Hit http://medibuntu.sos-sts.com feisty/non-free Packages                                            
Hit http://medibuntu.sos-sts.com feisty/free Sources                                                 
Hit http://medibuntu.sos-sts.com feisty/non-free Sources                                             
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US                                   
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US           
Get:11 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]          
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US   
Hit http://us.archive.ubuntu.com feisty Release                                
Err http://wine.lowvoice.nl feisty/main Packages                               
  Could not resolve 'wine.lowvoice.nl'
Hit http://us.archive.ubuntu.com feisty-updates Release  
Hit http://archive.ubuntu.com feisty-backports/main Packages                                                                
Get:12 http://ubuntu.iuculano.it feisty/thunderbird Packages [8785B]                                                        
Hit http://archive.ubuntu.com feisty-backports/restricted Packages                                                          
Hit http://us.archive.ubuntu.com feisty/main Packages                                                                       
Hit http://archive.ubuntu.com feisty-backports/universe Packages                                                            
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages                                                          
Hit http://archive.ubuntu.com feisty-updates/universe Packages                                                              
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages                                                            
Hit http://archive.ubuntu.com feisty-security/main Packages                                                                 
Hit http://archive.ubuntu.com feisty-security/restricted Packages                                                           
Hit http://archive.ubuntu.com feisty-security/universe Packages                                                             
Hit http://archive.ubuntu.com feisty-security/multiverse Packages                                                           
Hit http://us.archive.ubuntu.com feisty/restricted Packages                                                                 
Hit http://us.archive.ubuntu.com feisty/main Sources                                                                        
Hit http://us.archive.ubuntu.com feisty/restricted Sources                                                                  
Hit http://us.archive.ubuntu.com feisty/universe Packages                                                                   
Hit http://us.archive.ubuntu.com feisty/universe Sources                                                                    
Hit http://us.archive.ubuntu.com feisty/multiverse Packages                                                                 
Hit http://us.archive.ubuntu.com feisty/multiverse Sources                                                                  
Get:13 http://ubuntu.iuculano.it feisty/thunderbird Sources [37B]                                                           
Hit http://us.archive.ubuntu.com feisty-updates/main Packages                                                               
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages                                                         
Hit http://us.archive.ubuntu.com feisty-updates/main Sources                                                                
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources                                                          
Fetched 22.9kB in 8s (2561B/s)                                                                                              
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg  Could not resolve 'wine.lowvoice.nl'
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2  Could not resolve 'wine.lowvoice.nl'
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz  Could not resolve 'wine.lowvoice.nl'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
swarup@swarup-laptop:~$ 


```

I tried running TB from the terminal, but again nothing happened.

swarup@swarup-laptop:~$ thunderbird
swarup@swarup-laptop:~$ 

Do you think I should uninstall TB and get a fresh start? I wouldn't even know how to delete what I have now. Ubuntuzilla has a terminal command for uninstalling its version. Would that still work after we've added the repositories from that website, Iuculano's debian packages v7.04? 

Or if not an uninstall, then what should be done at this point?

---

### Post by r_l on 2007-08-27
> **swarup said:**
> I went to this site and followed the directions perfectly. First I downloaded the Ubuntuzilla downloader, and installed that. Then I went to a terminal window and typed the line they gave for installing Thunderbird. Everything seemed to go fine, and Thunderbird installed. But now, when I go to Applications -> Internet -> Thunderbird and click to open TB, it looks like it is trying to open something, but after around 20 seconds of trying, it just gives up and nothing opens. So what happened? Did I get a messed up version of the program somehow? I guess I'll have to uninstall it and try doing it some other way?

Oh, I forgot to mention, I had that one, too.  It turns out that I had scim installed and Tbird2 has problem with it.  I don't know if you have scim installed, but if you do, the workaround is mentioned in the FAQ

[http://ubuntuzilla.wiki.sourceforge.net/]("http://ubuntuzilla.wiki.sourceforge.net/")

Under the section: "[Thunderbird, Firefox] Thunderbird doesn't start at all. Segmentation Fault (Core Dumped) when running from terminal"

---

### Post by r_l on 2007-08-27
> **swarup said:**
> Many thanks to both of you. I'm going to go ahead now and put in terminal the lines Marjorix outlines. It should only take 5 minutes. I'll let you know what happened. 

So as I understand, this will all be done keeping the version of 2.0.0.6 I got from Ubuntuzilla installed. I'll let you know what happened in 5 minutes.

Ubuntuzilla keep a separate version of its own.  So you can get rid of other versions that you don't use - I uninstalled my old one (1.5+).  What I mean is  that the Ubuntuzilla install is not tracked by apt-get.

---

### Post by Majorix on 2007-08-27
I believe you should remove the version you installed using Ubuntuzilla. Cause when you try "thunderbird" in terminal it I guess boots the version from Ubuntuzilla. And you could be accidentally clicking their link instead of the new one.

---

### Post by swarup on 2007-08-27
> **r_l said:**
> Oh, I forgot to mention, I had that one, too.  It turns out that I had scim installed and Tbird2 has problem with it.  I don't know if you have scim installed, but if you do, the workaround is mentioned in the FAQ

[http://ubuntuzilla.wiki.sourceforge.net/]("http://ubuntuzilla.wiki.sourceforge.net/")

Under the section: "[Thunderbird, Firefox] Thunderbird doesn't start at all. Segmentation Fault (Core Dumped) when running from terminal"

Hey, thanks for the tip. I was really excited when you I saw this, because I DO run SCIM in my computer. And it is very important in the work I do, so I have to keep it. But the link you gave does offer a work-around. 

The problem is, that even with the work-around, TB is not starting up. 

Question: They offer to solutions to the SCIM problem there--(1) they show how to delete/disable SCIM; (2) they show a way of keeping SCIM enabled but working around it to start TB. 

Did you do (1) or (2)? 

#2 did not work for me, so I'm wondering whether perhaps you did #1?

> **Majorix said:**
> I believe you should remove the version you installed using Ubuntuzilla. Cause when you try "thunderbird" in terminal it I guess boots the version from Ubuntuzilla. And you could be accidentally clicking their link instead of the new one.

Do I have two separate versions of TB 2.0 loaded now? I hadn't realized that clearly in my mind. Because when we were doing this "adding the repos" yesterday, somehow I thought we were just filling in the gaps of what the Ubuntuzilla version was missing. So you mean to say that if I delete the Ubuntuzilla version, I'll still have another full version of TB ready to run? 

OK. Let's try this and see what happens.

If it still doesn't work, I may do a clean install with the Ubuntuzilla and see if RL's SCIM workaround works in that scenario without the repos we added. 

If I use Synaptic Package manager to uninstall completely including configuration files, will that uninstall any and all versions of TB currently in the computer, or will some remain that Synaptic Package manager doesn't see?

---

### Post by swarup on 2007-08-27
Actually, Ubuntu's routine update manager has just today (or yesterday?) added in the update to TB 2.0.0.6. So just now when I ran the update manager, it updated TB to 2.0.0.6. ...And now TB starts up just fine, and it has 2.0.0.6. (Before running the update manager, I uninstalled the Ubuntuzilla install, so just the 1.5.0.13 remained. And that started up just fine. Then I ran the Ubuntu update manager, which updated it to 2.0.0.6. And that also starts up fine.) --If I had only known Ubuntu was about to release this update into their own repositories!!! All this struggle would have been unnecessary. Whew. Thanks everyone for all your help, though. I certainly did learn quite a bit through all this. I guess in a certain way that always makes it worth while.

---

### Post by TeaSwigger on 2007-08-27
EDIT: lol too late. Glad it worked out :)

---

### Post by Majorix on 2007-08-27
> **swarup said:**
> Actually, Ubuntu's routine update manager has just today (or yesterday?) added in the update to TB 2.0.0.6. So just now when I ran the update manager, it updated TB to 2.0.0.6. ...And now TB starts up just fine, and it has 2.0.0.6. (Before running the update manager, I uninstalled the Ubuntuzilla install, so just the 2.0.0.13 remained. And that started up just fine. Then I ran the Ubuntu update manager, which updated it to 2.0.0.6. And that also starts up fine. --If I had only known Ubuntu was about to release this update into their own repositories!!! All this struggle would have been unecessary. Whew. Thanks everyone for all your help, though. I certainly did learn quite a bit through all this. I guess in a certain way that always makes it worth while.

Are you sure it was the feisty repos you downloaded TB from? You added the TB backports following the instructions I submitted...

Glad you got it working :)

---

### Post by r_l on 2007-08-28
> **swarup said:**
> Actually, Ubuntu's routine update manager has just today (or yesterday?) added in the update to TB 2.0.0.6. So just now when I ran the update manager, it updated TB to 2.0.0.6. ...And now TB starts up just fine, and it has 2.0.0.6. (Before running the update manager, I uninstalled the Ubuntuzilla install, so just the 2.0.0.13 remained. And that started up just fine. Then I ran the Ubuntu update manager, which updated it to 2.0.0.6. And that also starts up fine. --If I had only known Ubuntu was about to release this update into their own repositories!!! All this struggle would have been unecessary. Whew. Thanks everyone for all your help, though. I certainly did learn quite a bit through all this. I guess in a certain way that always makes it worth while.

Sorry that I come late cos the time difference, but I am glad that it works out for you :)
RL

---

### Post by swarup on 2007-08-28
> **Majorix said:**
> Are you sure it was the feisty repos you downloaded TB from? You added the TB backports following the instructions I submitted...

Glad you got it working :)

I was thinking it was the feisty repos, because it came through feisty's Update Manager icon (the one that appears periodically on the upper bar of the screen). But someone informed me today on another thread ([http://ubuntuforums.org/showthread.php?p=3268213#post3268213](http://ubuntuforums.org/showthread.php?p=3268213#post3268213)) [see posting #2, and then posting #4] that feisty's repos do not supply this upgrade and that it is actually the TB backports which would have done this. 

So I guess you are right, it must be the iuculano's feisty backport repository which did the trick. Although it didn't work when you and I were working on it together. As I say, it worked through an update through the Update Manager. Does use of the iuculano's feisty backport repository result in updates coming in through the Update Manager? That is what ultimately got it working.

By the way, I want to install TB 2.0.0.6 on my other computer (feisty) which is currently running 1.5.0.13, then would the best way be to just add the iuculano's feisty backport repository using the terminal commands you gave me? And if so, should I use feisty's Add-Remove application to remove the current 1.5.0.13 version first? One additional critical question: that computer has several TB profiles in it which I will be needing to link to the new 2.0.0.6. Will those 1.5.0.13-generated profiles work in 2.0.0.6? I have some vague memory of reading somewhere that profiles from old versions may not be compatible with 2.0.0.6.

---

### Post by nanotube on 2007-08-28
> **swarup said:**
> I was thinking it was the feisty repos, because it came through feisty's Update Manager icon (the one that appears periodically on the upper bar of the screen). But someone informed me today on another thread ([http://ubuntuforums.org/showthread.php?p=3268213#post3268213](http://ubuntuforums.org/showthread.php?p=3268213#post3268213)) [see posting #2, and then posting #4] that feisty's repos do not supply this upgrade and that it is actually the TB backports which would have done this. 

So I guess you are right, it must be the iuculano's feisty backport repository which did the trick. Although it didn't work when you and I were working on it together. As I say, it worked through an update through the Update Manager. Does use of the iuculano's feisty backport repository result in updates coming in through the Update Manager? That is what ultimately got it working.

By the way, I want to install TB 2.0.0.6 on my other computer (feisty) which is currently running 1.5.0.13, then would the best way be to just add the iuculano's feisty backport repository using the terminal commands you gave me? And if so, should I use feisty's Add-Remove application to remove the current 1.5.0.13 version first? One additional critical question: that computer has several TB profiles in it which I will be needing to link to the new 2.0.0.6. Will those 1.5.0.13-generated profiles work in 2.0.0.6? I have some vague memory of reading somewhere that profiles from old versions may not be compatible with 2.0.0.6.

tb 1.5 profiles should work in tb2. but make backups just in case before you play around with it. i personally didn't have any problems back when i upgraded from 1.5 to 2.0. ..

---

### Post by swarup on 2007-08-28
> **nanotube said:**
> tb 1.5 profiles should work in tb2. but make backups just in case before you play around with it. i personally didn't have any problems back when i upgraded from 1.5 to 2.0. ..

I see. Thanks very much.

---

