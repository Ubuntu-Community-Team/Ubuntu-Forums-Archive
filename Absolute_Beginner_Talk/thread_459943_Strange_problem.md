---
title: "Strange problem"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by IzaKamakazi on 2007-05-31
Hi guys, I'm afraid Ubuntu is a very new thing to me so my undersanding is very very basic.

I have recently installed the 6.06 server edition which seemed to go very well concidering my knowledge.I then proceeded to install Webmin, again with no issues.

My problem started when I tried to install and configure DNS with Bind.To be frank it all went wrong.Therefore I decided to re install and try again.After the install I had the following problem.

Trying to change to root by using the command su and then the root password tells me that the username or password is incorrect ( im not at my home P|C so I can't give exact terminology at present). Using sudo -i and entering the same password works ok.I have read that this is not an issue as sudo -i is the same or better than su anyway.Is this a normal thing for this to happen?

My main problem is that when I try to install Webmin now I can use the command cd Desktop to start the install from the desktop but it fails when Webmin actually tries to install saying I must have root access.......no problem I thought, using sudo -i I get root access but then cd Desktop command gives me an error saying no such file or directory and I cannot continue any further.I am therefore in a loop that I cannot break.

As I said earlier I have allready installed webmin on an earlier occassion but now it fails.The only thing I can think of that I may have influenced is the re install.....I can't remember wether I chose to use the full hard drive or another option that was something like use full hard drive with vm something or other??.

Has anyone got a clue what im talking about?  lol

Any advise would be very much appreciated as I cannot find any answers using my best mate Google.

Cheers

Kamakazi

---

### Post by rillip on 2007-05-31
a.  You shouldn't need to ever use 

su root

The prefered way is 

sudo [command]



I don't think your two errors are related.  I think we'll need the actual error webmin is producing to help further.

As for why you're getting incorrect password errors when you use su, have you set the root password?  Again, I don't recommend it, but by default the root password is not setup in such a way as for you to use the account.  IF you think you really WANT to (there's not a NEED) you could run 

sudo passwd root

Then you'll be able to use su.  But again, I think the issues are unrelated and don't recommend this.

---

### Post by IzaKamakazi on 2007-05-31
Hi Rillip,

Thanks for taking the time to try and help out.

I'm looking into getting some books on Ubuntu/Linux so I'll have a better undertstanding but in the meanwhile I hope you don't mind giving some pointers if you can.

So, if i use terminal to carry out a command that needs root permissions such as installing Webmin , I can just use the sudo command in front of anything I want to type?. I set a password on installation but if that isn't what you refer to when you said have i set the root password then i guess the answer would be no and I understand that doing so would not be advised.

I have just tried what you advised with the sudo command and Webmin installed correctly so thanks for clearing that up for me.

My project is to get an Ubuntu webserver and also DNS server installed to host my website from home so there will be many more hurdles to come before i get to grips with all this.

Are ther any good publication or websites you may have used on your journey that you would advise me to take a look at?.

Thanks again for any input.

Kamakazi

---

