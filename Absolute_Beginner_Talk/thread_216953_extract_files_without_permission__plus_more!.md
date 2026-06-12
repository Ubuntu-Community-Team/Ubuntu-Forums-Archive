---
title: "extract files without permission?  plus more!"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by bleep on 2006-07-16
I have a zip file.  I double clicked it, and it opened in the "Archive Manager".  I tried to extract it's contents into var/www.  But I do not have permission for this directory according to the warning.  How do I gain permission, it didn't ask me for a password like terminal does so that I could.  Isn't the 30 times it asked me for my password since installing enough?  And when I do need it to ask, it doesn't ask.

The people in chat kept saying !Sudo, but as far as I'm aware, there is no place to type sudo in the Archive Manager.  There was a password field, but it seemed to be for protected zip archives, not for where you're unzipping it to.

Also, when I open a file like the sources.list file, it opens, but it's read only.  I thought.. well maybe if I right click, it'll say "Open as root", or something.  That way, it'll ask me for a password, so that when it opens, it lets me edit, and not just read.  But that's not there either.

I'm just confused... do I have to do EVERYTHING with command line?  Say I'm building a website.  I can't just double click index.php, because it'll be read only.  I have to open it in command line with sudo gkedit ../path index.php?  If I have to use the command line to gain permission to extract, why would it let me open in the archive manager anyways?  Could the Archive Manager program be given root privlages?

This is my second time trying Ubuntu.  I thought I was on the right track getting all the codecs installed with easyubuntu (am I going to prison?), and getting LAMP running as well with only a few hours of tutorial searching and typing stuff into terminal.  But now I'm stuck in something as simple as editing and moving files...

Do webdesigners find it more productive to not even have the web folder open, and instead the command line?  ls, dir, cd, etc?  You edit a logo in gimp.. save it to desktop.. then open command line.. then type a command to move it to [www..](www..) then type password.. then test the page in firefox?

Is there a way that I can just double click files so I can edit them?  Or if that's unsafe, just be given full access to var/www, since all I'm doing in that folder is testing websites before uploading them to my host?

I must be missing something, because I can't get over the counter intuitive nature of having to look up commands for something as simple as opening or moving a file.  It doesn't even open in a new tab when you open from the command line, it opens up a new instance of gedit.

---

### Post by Denis on 2006-07-16
Since you are running your system as a normal user, you can't do things that require you to be a root user. 

I think you're making it very difficult for yourself because you're trying to work with files that are not in a directory you own. Why don't you save these websites somewhere in your home folder? If you do want to use /var/www it will be a lot easier if you are the owner of this directory. 

To change the owner of /var/www: 

[LIST]
[*]start nautilus as a root user: in the terminal type: "sudo nautilus"
[*]browse to /var and right click on the www directory
[*]go to the permissions tab and change the owner and group to your username
[/LIST]

This way you only need to start nautilus as a root in the terminal. There is no further need to use the command line interface. Make sure to close the "root nautilus" afterwards, so you can't make unwanted changes. 

Now you can extract and work with new files you place in /var/www as a normal user.

---

### Post by bluecherry on 2006-07-16
> **bleep said:**
> I have a zip file.  I double clicked it, and it opened in the "Archive Manager".  I tried to extract it's contents into var/www.  But I do not have permission for this directory according to the warning.  How do I gain permission, it didn't ask me for a password like terminal does so that I could.  Isn't the 30 times it asked me for my password since installing enough?  And when I do need it to ask, it doesn't ask.

Try running Automatix ([http://www.getautomatix.com](http://www.getautomatix.com)), it's a tool that automatically installs some very handy prog's/features.

One of them is Nautilus Scripts (make sure you check this box in Automatix)  and this is what you need.

Go to the folder where the file is and rightclick > Scripts > root-nautilus-here. This also works on your desktop.

This will open a folder in 'root mode', so if you double-click the *.zip you open it as root and therefore you can extract it to /var/www.

> **bleep said:**
> 
The people in chat kept saying !Sudo, but as far as I'm aware, there is no place to type sudo in the Archive Manager.  There was a password field, but it seemed to be for protected zip archives, not for where you're unzipping it to.

You do not need to set a password to extract the files, once you are running Archive Manager as root, the application has root priviliges.
> **bleep said:**
> 
Also, when I open a file like the sources.list file, it opens, but it's read only.  I thought.. well maybe if I right click, it'll say "Open as root", or something.  That way, it'll ask me for a password, so that when it opens, it lets me edit, and not just read.  But that's not there either.

This is where another Nautilus script comes in handy. Righ-click on the file and select >Scripts>gedit-root. This will open the file in gedit (basic gnome text editor) with root permissions.
> **bleep said:**
> 
I'm just confused... do I have to do EVERYTHING with command line?  Say I'm building a website.  I can't just double click index.php, because it'll be read only.  I have to open it in command line with sudo gkedit ../path index.php?  If I have to use the command line to gain permission to extract, why would it let me open in the archive manager anyways?  Could the Archive Manager program be given root privlages?

No you do not need the command line for everything. Only to access programs and files that you are not allowed to access by default. 

On Ubuntu (or other Linux) you are free to do as you please withing your /home/username/ folder. That is why you can open the .zip but you can not extract it to /var/www. You can extract it to /home/timo/www for example.

Other files like sources.list are only writeble by the admin (=root) because of security. 

> **bleep said:**
> 
This is my second time trying Ubuntu.  I thought I was on the right track getting all the codecs installed with easyubuntu (am I going to prison?), and getting LAMP running as well with only a few hours of tutorial searching and typing stuff into terminal.  But now I'm stuck in something as simple as editing and moving files...

Do webdesigners find it more productive to not even have the web folder open, and instead the command line?  ls, dir, cd, etc?  You edit a logo in gimp.. save it to desktop.. then open command line.. then type a command to move it to [www..](www..) then type password.. then test the page in firefox?

Is there a way that I can just double click files so I can edit them?  Or if that's unsafe, just be given full access to var/www, since all I'm doing in that folder is testing websites before uploading them to my host?

I must be missing something, because I can't get over the counter intuitive nature of having to look up commands for something as simple as opening or moving a file.  It doesn't even open in a new tab when you open from the command line, it opens up a new instance of gedit.
You can double-click -> edit the file as long as they are located in your /home/username folder.

The problem with Apache is that it defaults to /var/www/, and you don't have write permissions there.

Solution might be:
* Create a folder "www" in your /home/username/ directory
* fire up the terminal and type:
* "sudo cp /var/www/* ~/www/*"
* "sudo rm -fr /var/www" (this removes the www dir)
* "sudo ln --symbolic ~/www /var/www" 

This creates a link from /var/www/ to /home/username/www/. 
Apache will follow the link and use the files from /home/username/www.
You can save to /home/username/www, and doubleclick, etc... without having to worry about permissions.

Hope this helps you out.

---

### Post by christhemonkey on 2006-07-16
Would be better to run:
```
gksudo nautilus 
```

The reasoning is explained somewhere on the forums, i forget where...

---

### Post by foxjwill on 2006-08-05
I found the easiest way to do that is 
```
sudo file-roller -e [directory] [file]
```

---

### Post by theapeman on 2006-11-01
Please forgive what may seem a bit of a rant -- I mean no disrespect, truly.  It's just that this is my third day of using any form of Linux and and I have to say I'm baffled by this whole "permission" issue as well.  I'm trying out Ubuntu because I like the idea of being liberated from the tyranny of Microsoft, and to learn about Linux.  Obviously that makes me a total noob, although the three days it took me to configure my wireless network card definitely helped break me in.  One of the things I'd heard about Linux was that it gives the user freedom to configure their system however they want.  Rather than being constrained by the way Microsoft wants you to do things.  Nice idea, I thought.  

But here is where I lose the plot:  How can my own computer tell me that I don't have permission to do things to it?  It's my computer, right?  I installed the operating system.  It's all mine.  I installed every directory and file that exists on the hard drive.  If not for me, none of them would be there to tell me that I don't have permission to do these things.  *By default* I should have access to *everything.*  If the OS wants me to enter my password once at login, that's fine.  But after that I should be able to do whatever I want.  It's my laptop, for goodness sakes, not the computer with the nuclear launch codes on it.

So after three days of trying to get my wireless card to work, I finally succeed. I gleefully head to mozilla to get firefox 2.0.  I download the .tar file.  I go to extract it into the firefox folder where I assume it belongs, and ask it to overwrite the existing files, so as not to have a bunch of old files hanging around in there, and I'm told I don't have permission to do that.  If *I* don't, then exactly *who does?*  I bought the computer with my own money!  No one but me ever uses it!  Evidently I could extract it to my home folder, but then I have two instances of firefox on my computer and that just seems silly.  And it still means I'm a slave to my computer -- the very enslavement I thought I'd gone over to Linux to get away from!

Of course, there's probably a way to do it at the command line using sudo, but *I don't know what it is!*  Meanwhile, I'm staring at the "extract" dialog box in the GUI and it's telling me I don't have the right permissions to extract into the folder I want to extract.  But it's not even offering me a chance to prove that I *do* have permission.  (I do, I really do!)  Like, "enter password to extract" or something like that.  No link to a help file where I can find out how to give myself permission (bizarre concept) or a hint as to how to do it via the command line.  Nope.  Just "you don't have the right permissions" -- end of story. 

So I navigate to the help forums and find, unsurprisingly, that I'm not the only one frustrated by this.  But instead of finding out how to have "root access" on my own computer all the time, by default, *as I ought to*, I read about workarounds, tweaks, scripts, fixes, convoluted ways of tricking my laptop into thinking that I have permission to do the things that I should already be allowed to do!  I can install (if my computer lets me) this automatix thing and/or this nautilus thing... well, where does it end?  

I've mucked around with computers since before windows, so I understand the charm of the command line. And I certainly appreciate the Linux community and the whole free, open source ethos.  It's great.  That's why I'm here.  But honestly -- my computer is a tool.  I use it to get things done.  If I have to bang my head against a wall for three days to accomplish what a single keystroke did in Windows, then what was it all for?  Where's the freedom I was promised?

---

### Post by mahalie on 2007-08-22
I'm a noob, so I can't tell you the exact code and by now you probably know or have gone back to windows but you CAN operate in 'god mode' as root, that is. It's just not recommended. The crazy permission thing mostly helps you not screw something up by not paying attention (I need the reminder!!) and helps with security, which is why Linux systems have been far more secure than Windows, historically.

---

### Post by mahalie on 2007-08-22
> **Denis said:**
> Since you are running your system as a normal user, you can't do things that require you to be a root user. 

I think you're making it very difficult for yourself because you're trying to work with files that are not in a directory you own. Why don't you save these websites somewhere in your home folder? If you do want to use /var/www it will be a lot easier if you are the owner of this directory. 

To change the owner of /var/www: 

[LIST]
[*]start nautilus as a root user: in the terminal type: "sudo nautilus"
[*]browse to /var and right click on the www directory
[*]go to the permissions tab and change the owner and group to your username
[/LIST]
(...)

Now you can extract and work with new files you place in /var/www as a normal user.

Ah, that's a missing link I've been needing. is this the same as CHOWN username /var/www ?

---

