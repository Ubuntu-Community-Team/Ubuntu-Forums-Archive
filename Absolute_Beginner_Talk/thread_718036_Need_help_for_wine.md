---
title: "Need help for wine"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by raz1n on 2008-03-07
Ok i'm extremely new to the whole linux thing and i dont know how to do anythng really. I'm trying to play wow on my computer which is running Linux Ubuntu 7.10 and i've tried entering the commands on the Terminal from other forum posts and the wine website itself but everytime i try it it tries connecting to what i entered in but it always times out and keeps retrying with the same outcome. someone please help

---

### Post by raz1n on 2008-03-07
All of the commands i've entered in the Terminal were attempts at trying to install wine, I wasnt very specific on what i just posted >_<

---

### Post by Crooksey on 2008-03-07
In the gaming forum there is a WoW thread, discussing installation and post installation.

---

### Post by Daveth on 2008-03-07
yes, I agree, you need to browse this

[http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)

throughly, see what wine version runs best with WOW, then go find it from the wine site. It generally behaves itself once loaded, though if you get it running it is sometimes best to lock your version down- I find wine upgrades sometimes break your carefully crafted work!

---

### Post by raz1n on 2008-03-07
I've read that and tried it but i can't get past the first step. It says:
1. Open a terminal(also called a konsole, CLI, and command prompt) and choose one of these two commands to run, based on your version of Ubuntu:

For Ubuntu Gutsy Gibbon (7.10)
Code:

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

but when i enter the command in the terminal it can never connect to [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list. It always times out or fails to connect to the network.

---

### Post by Daveth on 2008-03-07
this

[http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)

in a browser gets you to a download page. If you are running gutsy 32 bit you will need v.0.9.56 i386. This will give you a .deb file. Download to your home directory somewhere, then in nautilus / file manager, select the file, right click, properties, permissions, and check the execute as a file as a program box. Right click again and choose the install with the gdebi package installer. This should install wine, placing all the dependencies where they need to go, and making you a fake C;/ drive in /home.
Then follow the guide.

---

### Post by JoshuaRL on 2008-03-07
Alright, you probably need to add the repo key first.  Try:
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```

Then do the rest of the steps.

---

### Post by kwacka on 2008-03-07
enable the universe repository and then either use synaptic or 'sudo apt-get install wine'

Also check out the wine pages where there is plenty of information on installing WoW.

---

### Post by raz1n on 2008-03-07
ok like I said earlier I am a complete noob and i have no idea what any of you are talking about...think of me as your grandma and try explaining it that way.

---

### Post by raz1n on 2008-03-07
Also when i click on the link that you've posted it tries loading the page for awhile and then says:

Unable to connect

      

      
      
      

      
        
        

          

Firefox can't establish a connection to the server at wine.budgetdedicated.com.

        


        
        


    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

---

### Post by JoshuaRL on 2008-03-07
Is your internet working properly?  I know you're posting here, but are you doing it from Ubuntu?

And try that repository key step I posted above, I think that might be your issue.

---

### Post by kwacka on 2008-03-07
click on 'system'  --> Administration --> Synaptic package manager. Enter password.

Now click on 'Settings' --> 'reporitories'. Ensure that the 'universe' box is checked (probably won't do any harm to click the others as well, plus the third party tag & boxes.

Close. Now tick the reload icon, and wait until finishes.

Click on 'search', type in 'wine', check the wine box that comes up & apply.

If you have a windows installation file right-click on it and select 'open with' then wine.

Any problems come back.

---

### Post by JoshuaRL on 2008-03-07
> **kwacka said:**
> click on 'system'  --> Administration --> Synaptic package manager. Enter password.

Now click on 'Settings' --> 'reporitories'. Ensure that the 'universe' box is checked (probably won't do any harm to click the others as well, plus the third party tag & boxes.

Close. Now tick the reload icon, and wait until finishes.

Click on 'search', type in 'wine', check the wine box that comes up & apply.

If you have a windows installation file right-click on it and select 'open with' then wine.

Any problems come back.

The problem with that is that it installs only a certain version of Wine, and doesn't update it.  If that's the wrong version, he will have to fix the install source anyway.  For instance, the current version in the Ubuntu repos is version 0.9.43, while the newest version directly from Wine is version 0.9.57.  So if you either need to install a specific version of Wine, or want the newest so that the most programs will work with it, there's better ways.

---

### Post by raz1n on 2008-03-07
my internet is working fine, except for that website i dont know what the deal is but for some reason i just cant connect to it....:mad:

---

