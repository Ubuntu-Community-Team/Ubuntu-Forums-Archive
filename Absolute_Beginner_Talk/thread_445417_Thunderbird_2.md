---
title: "Thunderbird 2"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Sabar on 2007-05-15
Well I started out posting a question on printers but I think I have that figured out. I'll ask how to scan later. :) 

Ok, I downloaded the new version of Thunderbird from the Mozilla web site.  I now have it on my desktop. I believe I have it unzipped.:confused:  Well there is now a file along with a box sitting there. . Now here is my question. how do I install it? 

I already have Thunderbird 1.5 set up and running. I don't have it like I want it yet but it is there.  am I going to write over that?

I really do not have a clue what i am doing here so if some one can please help me out on this and be VERY specific on what to do I would really appreciate it.  I read the Mozilla web site instructions and well I think it would be very helpful if you knew even just a little bit about what you are doing.

Oh about the printer. after installing the driver can I delete the file off my desktop?

the other thing about Thunderbird 2 that I can not figure out is. how can I set it up for two separate users? so we do not share the same in box or out box? Once again please speak slowly we are talking about a compleat Ubuntu dunce here but guys I sure am trying.

Sabar

P.s. any way to get a neat penguin pic for my profile?

---

### Post by crimesaucer on 2007-05-15
I installed it using this guide:

[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

Basically, all you have to do is 4 different terminal commands and it downloads the new Thunderbird 2.0, unzips it, and puts it in your /opt file. Then it creates some symbolic links to use your new Thunderbird. Then you run it.

```
wget -c http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.0/linux-i686/en-US/thunderbird-2.0.0.0.tar.gz 

```

```
sudo tar -C /opt -zxvf thunderbird-2.0.0.0.tar.gz 
```

```
sudo dpkg-divert --divert /usr/bin/mozilla-thunderbird.ubuntu --rename /usr/bin/mozilla-thunderbird 
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/mozilla-thunderbird
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird
```

```
thunderbird
```

Then all you have to do is change your launcher to the correct name. Everything is explained in that guide.

---

### Post by n8bounds on 2007-05-15
Don't reinvent the wheel.

[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

Always check the help.ubuntu.com wiki first.  Tried and true methods for common problems usually end up in the community docs there.

Yes, you probably can delete it.  Not sure?  Rename it/move it and see what happens.  Learning linux is fun, experiment for yourself.  

Best thing for multi-user computing is to add another system user to your PC, instead of trying to run the same program for two different people from the same system user.  If that's not what you want, maybe you could just add both email accounts?

---

### Post by crimesaucer on 2007-05-15
Same guide I used, it was super easy. And as for deleting the old version, you don't have to delete it at first because it creates the links to the new version. I don't know about your other question of multiple users.

---

### Post by alienexplorers on 2007-05-15
I just downloaded the tar file from mozilla.  un-tarred it in my /home partition.  enter /home/yourname/thunderbird in the terminal or create a desktop icon.  I did not delete my old version of thunderbird incase of any problems with the new version.

---

### Post by Derevko on 2007-05-16
You can find a feisty backport in my repository [http://ubuntu.iuculano.it/](http://ubuntu.iuculano.it/)

[http://ubuntu.iuculano.it/dists/feisty/thunderbird/](http://ubuntu.iuculano.it/dists/feisty/thunderbird/)

---

