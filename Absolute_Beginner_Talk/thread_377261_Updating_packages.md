---
title: "Updating packages"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2007-03-05
I have one particular package in one repo I want to install. That repo is listed as being for Edgy.

However, it has 'unresolveable dependencies'.

These 4 dependencies are spread through other repos.

They seem to be showing 'latest version' numbers, that are less than are listed by the unresolveable dependencies from my wanted package.

I have installed Dapper. So is it unsuprising that this is happening?

I tried reinstalling and / or upgrading the dependencies, but they only went as high as the originally listed 'latest version'.

Is there some way I can pick and choose higher numbered versions just to get my one 'wanted' package installed (there are only 4 dependencies) or should I be ditching Dapper and going for Edgy wholesale.

I went for Dapper x64 originally because I am a complete linux novice, and thought it would be 'safer'.

---

### Post by Dr. Nick on 2007-03-05
You should have this problem unless you started playing with 3rd party repos, or used a few edgy reps at one point, Is either the case?

it appears you are trying to install from a edgy repo and the dependencies come from a dapper repo, this is usually a bad idea. I would change all repos to edgy then try it, dapper will not get newer version of its apps unless its a security fix in  most cases. 


Try sing aptitude aswell, its safer then synaptic, but must be done from the command line

eg

sudo aptitude install packagename

---

### Post by ecs_pf5 on 2007-03-05
Both.. it's a 3rd party repo made for edgy containing 'nspluginwrapper'. I was trying to get flash player working in firefox on x64.

link to my [original post](http://ubuntuforums.org/showthread.php?t=377166) for reference.

Will try your suggestions - thanks

---

### Post by Dr. Nick on 2007-03-05
what you can try doing is switching all repos to edgy, installing it and get it running, then set them back to dapper if you want to avoid any additional edgy packages. That can be done sparingly , but if you find yourself wanting more edgy versions I would just do a total upgrade.

---

### Post by Dr. Nick on 2007-03-05
Just checked your original post , I would do a full  update, the libc6 is a dangerous package to play with a dn upgrading it could break alot of other programs.


That or look for a dapper version if possible, I never used that program before. But I have goofed up libc6 and its no fun lol

---

### Post by ecs_pf5 on 2007-03-05
I've learnt more Linux this evening than I have in the last ten years, I swear :-) 

Full update it is.

---

