---
title: "Installing Java 1.5.0 from the java self extracting file??"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-12
I'm trying to add the Firefox java plugin and I don't understand the instructions that java had for the self extracting file.

Can anyone tell me how to do this. I have also installed EasyUbuntu and automatix2 (I hope they don't conflict) and java still isn't working.

---

### Post by PriceChild on 2006-10-12
Could you try using this wiki?

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

You will learn how things work more on your system instead of using automaix or EasyUbuntu.

It may look scary at first but go for it! :)

(btw firefox plugin is under Section 9)

---

### Post by crimesaucer on 2006-10-12
this is m first official day of trying to creat my xubuntu os, when you say use wiki, is that a wiki page with a guide on it of the faq's of a beginner and what they need to install and how?

And what is the problem with automatix2 and EasyUbuntu, I ask this because I want to learn the reasons why certin things are better for my computer and all of the inner workings...and so on.

thanks.

---

### Post by PriceChild on 2006-10-12
That wiki includes instructions on how to do what you're asking.

Automatix and EasyUbuntu are great programs.

Personally i prefer installing manually installing programs because i learn more about how the system works, and how to fix it if(when) it goes wrong.

Also, automatix and easyubuntu don't crash well, which can lead to problems.

---

### Post by Toxicity999 on 2006-10-12
Completely agreed, Those two progams are sort of our OH YEAH! To windows, super new users tend to find them like them. But, they get confused later. To me (I was new once too, but before automatix was more than a little script, and before Easy Ubuntu even existed...) The biggest thing is for larger game like JRE skim the official repos it *is* there now after a huge lisencing issue was solved we can now officially toss it out there for easy fetching.

sudo apt-get install sun-java5-bin sun-java5-jre sun-java5-plugin

for instance would get you everything you needed including a firefox plugin (optional of course.)

---

### Post by crimesaucer on 2006-10-12
So just that terminal command is needed, because when I tried to install from the plug in option off of Firefox, the instructions for the "self extracting file for jre 1.5.0 was really confusing.

I also read that page you linked me too and it didn't say anything for xubuntu 6.0.6

I do plan on learning "the real" ways to use xubuntu, but right now I had a complication with my dual boot and I ended up just wiping out WinXp and so having a quick way to enjoy my videos/audio/mp3s is necessary.

I also have tried to install flash, I downloaded it and opened it and I know I haven't done something right becuase it still is not working.

Anyway, I just joined a xubuntu forum so hopefully between the two of these forums and some suggested pages, I'll figure this out.

---

### Post by crimesaucer on 2006-10-12
I wrote that code in to terminal and I got: command not found

I have all of my repositories active (I think), plus the addition of the automatix main.

So can anyone link me to a total page of terminal code for xubuntu 6.0.6 xfce desktop.

thank.

---

### Post by PriceChild on 2006-10-12
> **Toxicity999 said:**
> sudo apt-get install sun-java5-bin sun-java5-jre sun-java5-pluginYup.. do this! Even fine on xubuntu.

---

### Post by crimesaucer on 2006-10-12
I wrote that and got: command not found

Was I supposed to write just that command? Or was that just one line out of a  procedure that I should know about.

---

### Post by PriceChild on 2006-10-12
> **crimesaucer said:**
> I wrote that and got: command not found

Was I supposed to write just that command? Or was that just one line out of a  procedure that I should know about.
do this:

```
sudo apt-get update
sudo apt-get install sun-java5-bin sun-java5-jre sun-java5-plugin
```

---

### Post by Sef on 2006-10-12
> 
Code:

sudo apt-get update sudo apt-get install sun-java5-bin sun-java5-jre sun-java5-plugin



Have you enabled universe and multiverse in the repositories?  If not, then [click here.]("https://help.ubuntu.com/community/Repositories/Ubuntu")

Universe is GPL software not part of the main repositories.  Multiverse is non-GPL software.

(Ubuntu is strictly GPL software.)

---

### Post by crimesaucer on 2006-10-12
Reading package list...Done
Building dependency tree...Done
E: Couldn't find package sun-java5-bin

I also think one of the problems I'm having right now is a GPG error in terminal that says, that it is not verifing the [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release: because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C

any help for either. Maybe I'm tired and not thinking smartly, maybe I should take a rest for a little bit and read up on everything latter.

thanks for trying to help.

---

### Post by crimesaucer on 2006-10-12
Yes Sef, I think I did it correctly, I have all of my repositories check in my synaptic manager. I also added the automatix repository on my sources.list

...and I just re-istalled the public gpg key for automatix and everything said it installed so I hope I did it right, I don't know right now, I need to sleep and start agin latter, thanks for the help.

yeh...and that java code still gets me the "command not found"

thanks anyway,latter
-c.

---

