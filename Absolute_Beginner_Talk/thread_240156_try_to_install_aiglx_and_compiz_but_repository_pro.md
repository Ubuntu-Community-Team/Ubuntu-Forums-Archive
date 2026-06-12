---
title: "try to install aiglx and compiz but repository problem"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by kpham.p on 2006-08-20
hello all,
I try to install aiglx and compiz by following some of the instruction that posted on ubuntuforums.org.  however when I added the following repository: > deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main aiglx
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main aiglx

then run :
>  sudo apt-get update
and I get the following error:
> 
...
...
Reading package lists... Done
W: GPG error: [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release: The following signatures co uldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED 8A569E
W: You may want to run apt-get update to correct these problems

any idea guys?
thanks
Kpham.p

---

### Post by kebes on 2006-08-20
You need to manually add the key for that repository so that your machine will trust it. Look at the instructions on this page:
[http://xgl.compiz.info/](http://xgl.compiz.info/)

Follow them carefully. In particular, you'll see that they tell you to run:
```
wget http://ubuntu.compiz.net/quinn.key.asc -O - | sudo apt-key add -
```

The "wget" part is a commandline way of downloading a particular file. In this case you're downloading a "key" that identifies the repository. Then this key is being given as an argument to "apt-key" which will add the key to your list of "trusted sites". The second command must be run with "sudo" because it is an administrator-level change.

After adding the key, do "sudo apt-get update" again and try to install.

---

### Post by Uncle Spellbinder on 2006-08-20
Use: 
*deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx*
or
*deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx*
Or both.


DO NOT....I repeat... [color=#CC0000]**DO NOT**[/color] add **ubuntu.compiz.net** or **xgl.compiz.info** to your sources list. 

Or at least comment them out if you insist on adding them.


See here:  [**_Community Compiz+etc. Packages_**](http://www.beerorkid.com/compiz/)

---

### Post by kpham.p on 2006-08-21
Awesome, thanks guys.  I will try it again and let you guy know if I run across any trouble ;)

---

### Post by Uncle Spellbinder on 2006-08-21
***Repo update:***

It seems as the repos are back and "good to go"

See here: 
[_**xgl.compiz.info/ubuntu.compiz.net repos are back up**_](http://www.compiz.net/viewtopic.php?pid=27483#p27483) 
and 
[_**Community Compiz+etc. Packages**_](http://www.beerorkid.com/compiz/)

---

