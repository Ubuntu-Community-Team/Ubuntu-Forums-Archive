---
title: "Installing Cedega o.O"
date: 2005-06-25
forum: Absolute Beginner Talk
---

### Post by RoflKopter on 2005-06-25
Ive tried to find this in the forum, I went through about 3 pages looking for it. 
I tried to follow this guide 
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45)
but when I do it I get this 
```

List of profiles (b to go back):

0 ) cvscedega_head
Enter choice:
0


Running Profile : cvscedega_head
Enter root Password:
su: Authentication failure
Sorry.

``` 

Thats using "sh WineCVS.sh"
Using "sudo sh WineCVS.sh" I get this.

```
--------- Error log - file /home/roflkopter/.WineCVS/sources/cvscedega/ErrorLog : ---------
/home/roflkopter/.WineCVS/Functions/RunWineCVS: line 728: cvs: command not found

Error in CVS checkout

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

``` 

What do I do? I had wine installed but I couldent get steam to work with it. So I read that cedega (winex I guess) can get steam working. If im wrong please correct me.

---

### Post by RoflKopter on 2005-06-25
Okay I got cedega installed. I found a .rpm and I used "alien --to-deb cedega*.rpm"
then "alien -i cedega*.deb" and I guess it installed

```
(Reading database ... 58550 files and directories currently installed.)
Preparing to replace cedega 20050217-1 (using cedega_20050217-1_i386.deb) ...
Unpacking replacement cedega ...
Setting up cedega (20050217-1) ...
``` 

But I dont know how to use it, I goto a folder and type "cedega <gamefilename>.exe" and it tells me 

```
bash: cedega: command not found
``` 

Did I do somthing wrong?

---

### Post by Kyral on 2005-06-25
The CVS Version of Cedega (the one you are using) is a bit lacking in features. To get the full version you need to pay at least 15 bucks (I say at least b/c its a subscription at $5/month) . But you get updates and a really great frontend called Point2Play, not to mention DEB packages for both and the ability to vote for what features come out in the next version of Cedega.

And believe me, the price is worth it :D

[http://www.transgaming.com](http://www.transgaming.com)

---

### Post by RoflKopter on 2005-06-25
... looks like im going to haft to figure out a way to get 15$ then.

---

