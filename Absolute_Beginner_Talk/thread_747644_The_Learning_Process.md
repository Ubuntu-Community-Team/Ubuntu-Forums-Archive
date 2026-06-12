---
title: "The Learning Process"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by dpilot83 on 2008-04-06
Well, I'm essentially a first time Linux user here. I have Windows XP, Vista and Ubuntu 7.1 installed in a triple boot configuration. I use Windows XP as my primary operating system and I'm just using Vista and Ubuntu on an experimental basis.

So far I'm pretty excited about Ubuntu. One really nice feature is the forums. Although I have just registered today and this is my first post, I've already fixed several issues with the Ubuntu forums.

My primary issue at this point is that I really don't know why the things I'm doing end up fixing the problems I'm having. For example, When I installed a flash player I installed gnash of the two choices because open source is always better right? Well, I couldn't view a youtube video and a quick search on the Ubuntu forums confirmed that gnash was the problem and that I should stick with the Adobe version for at least the time being. So I searched for how to remove gnash and install Adobe and I quickly found the following advice:

sudo apt-get install flashplugin-nonfree
sudo apt-get remove gnash

Guess what, it worked great, but what in the world did I just do? Yes, I can do another search and figure out why what I just did worked so well but isn't there a place where I can go and just sit and study for awhile and learn what sudo or apt-get means or how Ubuntu knows where to go to find the flash player installation files when I type "sudo apt-get install flashplugin-nonfree" and how am I to know that it's "flashplugin-nonfree" rather than "flashplugin" or "adobeflash". I guess what I'm saying is, this is good stuff, but where can I go to study rather than searching forums all day? Thanks.

---

### Post by Crafty Kisses on 2008-04-06
[Ubuntu Documentation]("https://help.ubuntu.com/community/") is really good, and this is what you did, when you did this:
```
sudo apt-get install flashplugin-nonfree
```
You installed Flash, then when you did this:
```
sudo apt-get remove gnash
```
You removed Gnash. :)

---

### Post by bsharp on 2008-04-06
I would also recommend getting a book on Ubuntu, I got [Ubuntu Unleashed]("http://www.amazon.com/Ubuntu-Unleashed-Andrew-Hudson/dp/0672329093"), which is a great book that walks you through basic installation up to compiling and installing kernels.  It is a little outdated (6.06 Dapper), but the basic principals are the same.

---

### Post by JoshuaRL on 2008-04-06
The link in my sig "Learn the Terminal" is a great one for learning what a lot of the commands do and mean.

Also, try the Ubuntu Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
Ubuntu Guide:  [http://ubuntuguide.org](http://ubuntuguide.org)
aysiu's guides:  [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
and Ubungu Geek list of free ebooks:  [http://www.ubuntugeek.com/free-ubuntu-linux-e-books.html](http://www.ubuntugeek.com/free-ubuntu-linux-e-books.html)

---

### Post by coolen on 2008-04-06
APT (the Advanced Packaging Tool) uses online repositories. When you type apt-get install <packagename>, or install something from Synaptic, or whatever, it fetches the latest version of that package from the repositories it knows about.

These repositories are defined in the file /etc/apt/sources.list, mostly. You can set them from the GUI in System -> Administration -> Software Sources. After you add a repository, you have to either run apt-get update, or reload from the GUI. APT will then go and get package information from each of the repositories you have defined.

As for knowing the package name, it's just a matter of knowing it, I'm afraid. Most will be more obvious than that (for a lot of programs, the name will so). If you get stuck, search for it in Synaptic. It shouldn't be too hard to find.

You'll forgive us forum folk for not explaining in too much detail what's going on. A lot of people just want it to work, which is fair enough. It's refreshing to come across someone who wants to know what these commands are doing :)

---

### Post by seth556 on 2008-04-06
Linux takes a bit of work till you understand how it works. The easiest way is to make yourself not think of it working like Windows, it's completly different. 

The next biggest thing for me was how apt works and how useful it is. There's not really a need to be downloading different programs off the internet to install. Use add/remove programs or Synaptic to install them. Mostly likely the program is already there if it runs on linux. However there's a few programs that aren't there and you can usually download a deb or source file to install it.

Third thing is understanding how the command line works. It's not like Windows where it gives you "unreadable" type. It's almost always easy to understand with some reading. Then with commands, their usually regular english words like "install", "remove" and "search." Then a few that you need to learn like cd to change the directory and ls to list everything in the folder.

Then the people on here are here to help you.

---

### Post by dpilot83 on 2008-04-06
Thanks for all the excellent responses. You guys have pointed me in the right direction I think. I've already got enough reading material to keep me going for weeks. Thanks again.

---

### Post by matt79 on 2008-04-06
I too have a book but I find the tab key to be very useful.
 If I type "apt-get install" and than hit the tab key twice it will give me 23664 options to install. To many to look through (although I have done it)
but you can type "apt-get install desk" then hit the tab key twice it will only give 6 options. All of the options start with desk. You can also use the tab key to finish commands. If I forget the sudo command I can type "su" and hit the tab key twice it will give me six options that start with su. Among them I can find the "sudo" command. The number of options will vary depending on the machine that is used and updates that are installed but it should work on any machine.

---

### Post by dpilot83 on 2008-04-07
> **matt79 said:**
> I too have a book but I find the tab key to be very useful.
 If I type "apt-get install" and than hit the tab key twice it will give me 23664 options to install. To many to look through (although I have done it)
but you can type "apt-get install desk" then hit the tab key twice it will only give 6 options. All of the options start with desk. You can also use the tab key to finish commands. If I forget the sudo command I can type "su" and hit the tab key twice it will give me six options that start with su. Among them I can find the "sudo" command. The number of options will vary depending on the machine that is used and updates that are installed but it should work on any machine.

Mmmm, good advice, thanks.

---

