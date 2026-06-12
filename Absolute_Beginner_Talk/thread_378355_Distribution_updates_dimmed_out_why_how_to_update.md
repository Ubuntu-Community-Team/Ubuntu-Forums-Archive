---
title: "Distribution updates dimmed out: why? how to update?"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by SteveHoffmanUK on 2007-03-07
Edgy desktop system here.

Recently I've noticed that when I receive notification of updates, the panel shows them in two categories:
1. Important security updates
2. Distribution updates

In category 1, the boxes are ticked by default; In category 2, the tick boxes are dimmed-out and I can't tick them. For example, currently in category 2 are libggl2 and Mplayer. Two questions:

1. What is the point of showing items with tick boxes if you can't tick them?
2. How do I update the category 2 items?

---

### Post by Kateikyoushi on 2007-03-07
Copy these two lines to the terminal and let us know about their output.

```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by SteveHoffmanUK on 2007-03-07
OK. Did that, here are the results:
```
Get:1 http://archive.ubuntu.com edgy Release.gpg [191B]       
Ign http://archive.ubuntu.com edgy/main Translation-en_GB     
Ign http://archive.ubuntu.com edgy/restricted Translation-en_GB
Ign http://archive.ubuntu.com edgy/universe Translation-en_GB  
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_GB
Get:2 http://archive.ubuntu.com edgy-security Release.gpg [191B]
Ign http://archive.ubuntu.com edgy-security/main Translation-en_GB
Ign http://archive.ubuntu.com edgy-security/restricted Translation-en_GB
Ign http://archive.ubuntu.com edgy-security/universe Translation-en_GB
Ign http://archive.ubuntu.com edgy-security/multiverse Translation-en_GB
Get:3 http://archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_GB
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_GB
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_GB
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_GB
Get:4 http://archive.ubuntu.com edgy-backports Release.gpg [191B]
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_GB
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_GB
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_GB
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_GB
Hit http://archive.ubuntu.com edgy Release                     
Hit http://archive.ubuntu.com edgy-security Release            
Hit http://archive.ubuntu.com edgy-updates Release                              
Hit http://archive.ubuntu.com edgy-backports Release                            
Hit http://archive.ubuntu.com edgy/main Packages                                
Hit http://archive.ubuntu.com edgy/main Sources                
Hit http://archive.ubuntu.com edgy/restricted Packages         
Hit http://archive.ubuntu.com edgy/restricted Sources          
Hit http://archive.ubuntu.com edgy/universe Packages           
Hit http://archive.ubuntu.com edgy/universe Sources            
Hit http://archive.ubuntu.com edgy/multiverse Packages         
Hit http://archive.ubuntu.com edgy/multiverse Sources          
Hit http://archive.ubuntu.com edgy-security/main Packages      
Hit http://archive.ubuntu.com edgy-security/main Sources       
Hit http://archive.ubuntu.com edgy-security/restricted Packages
Hit http://archive.ubuntu.com edgy-security/restricted Sources 
Hit http://archive.ubuntu.com edgy-security/universe Packages  
Hit http://archive.ubuntu.com edgy-security/universe Sources   
Hit http://archive.ubuntu.com edgy-security/multiverse Packages
Hit http://archive.ubuntu.com edgy-security/multiverse Sources 
Hit http://archive.ubuntu.com edgy-updates/main Packages       
Hit http://archive.ubuntu.com edgy-updates/main Sources        
Hit http://archive.ubuntu.com edgy-updates/restricted Packages 
Hit http://archive.ubuntu.com edgy-updates/restricted Sources  
Hit http://archive.ubuntu.com edgy-updates/universe Packages   
Hit http://archive.ubuntu.com edgy-updates/universe Sources    
Hit http://archive.ubuntu.com edgy-updates/multiverse Packages 
Hit http://archive.ubuntu.com edgy-updates/multiverse Sources  
Hit http://archive.ubuntu.com edgy-backports/main Packages     
Hit http://archive.ubuntu.com edgy-backports/restricted Packages
Hit http://archive.ubuntu.com edgy-backports/universe Packages 
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages
Hit http://archive.ubuntu.com edgy-backports/main Sources      
Hit http://archive.ubuntu.com edgy-backports/restricted Sources
Hit http://archive.ubuntu.com edgy-backports/universe Sources  
Hit http://archive.ubuntu.com edgy-backports/multiverse Sources
Get:5 http://us.archive.ubuntu.com edgy Release.gpg [191B]     
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_GB
Hit http://us.archive.ubuntu.com edgy Release
Hit http://us.archive.ubuntu.com edgy/universe Packages
Fetched 5B in 3s (2B/s)
Reading package lists... Done

```

Hope this means something to you...

---

### Post by Kateikyoushi on 2007-03-07
Yes it means you are up to date, now the second line.

---

### Post by SteveHoffmanUK on 2007-03-07
> now the second line.

Sorry, but I don't understand: what do you mean by "now the second line"?

If I am up to date, why are those two items shown as Distribution Updates as a part of "Updates Available"?

Thanks for your help in this.

---

### Post by Kateikyoushi on 2007-03-07
Your package list is up to date, but you stil have to install those packages, the updater does not do this because it requires to remove some packages which are not compatible with the update. That is why those are dim.

This command makes the distibution update.
```
sudo aptitude dist-upgrade
```

---

### Post by SteveHoffmanUK on 2007-03-07
Kateikyoushi:

Thanks very much. I did that and everything got updated.

Does that mean that any time I find these "Distribution Updates" items, I need to run that command in Terminal?

Very much appreciate your help! =D>

---

### Post by fred_moabit on 2007-03-09
yeah, i also don't quite get it yet... i upgraded to edgy... from dapper to edgy.

same thing here, so i must open a shell and type in  these cmds everytime i see dimmed out items in my update manager?

is there an obvious function i am failing to see right now?

---

