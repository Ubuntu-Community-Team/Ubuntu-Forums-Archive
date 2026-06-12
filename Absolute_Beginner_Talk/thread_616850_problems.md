---
title: "problems"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by deepblue80 on 2007-11-18
hello
i am having problems with the package manager/synaptic manager in Fiesty Fawn.

i get this message when i try to go to the Add/Remove option to launch the package manager
[B][I]Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.[/I][/B]

i tried to add the multimedia repository and i think its broken down for some reason.
Then when i open synaptic manager, i get this:

[I][B]E: Type &#8216;--21:07:45--&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.[/B][/I]

Anyone know what to do?

---

### Post by Paul820 on 2007-11-18
> sudo apt-get update and sudo apt-get install -f

Did you issue those commands in the terminal like it told you to? Don't put the **and** in the middle though, do one then press enter and then do the other.

---

### Post by Beaucephus on 2007-11-18
Youre sources.list file is busted.  If you can post the full text of the file we can help you correct it as the error message asks.  Your options are fixing it or restoring the file from a backup.  The above commands will not work until the file is corrected.

---

### Post by deepblue80 on 2007-11-18
> **Beaucephus said:**
> Youre sources.list file is busted.  Either fix it or restore it from backup.

i have no clue on how i do that? any pointers?

---

### Post by deepblue80 on 2007-11-18
> **Paul820 said:**
> Did you issue those commands in the terminal like it told you to? Don't put the **and** in the middle though, do one then press enter and then do the other.

i am sure i just followed detailed descriptions as i a newbie to ubuntu. but i think i must av missed something, but now i cant open either the package manager or the synaptic? what do i do next?

---

### Post by jw5801 on 2007-11-18
Can you post the output of the following two commands? ```
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by deepblue80 on 2007-11-18
> **jw5801 said:**
> Can you post the output of the following two commands? ```
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/medibuntu.list
```
[B][I]
output of the command cat/etc/apt/sources.list
[/I][/B]
deep@deep-desktop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse


Output of the second command:-

deep@deep-desktop:~$ cat /etc/apt/sources.list.d/medibuntu.list
--21:07:45--  [http://www.medibuntu.org/sources.list.d/fiesty.list](http://www.medibuntu.org/sources.list.d/fiesty.list)
           => `fiesty.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Connecting to www.medibuntu.org|87.98.242.10|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
21:07:45 ERROR 404: Not Found.


sounds gobbledegook to me but hopefully should make sense to you!

---

### Post by jw5801 on 2007-11-19
Makes perfect sense to me! :p

Ok for some reason the medibuntu site recommends you add the repositories using a wget, except it returns a 404 - not found for feisty. Which is odd and probably should be reported to them, we can fix it though, just run the following commands and then you'll be cooking with gas!
```
sudo rm /etc/apt/sources.list.d/medibuntu.list
echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
sudo apt-get update
```Then continue as you were!

EDIT: If apt-get update returns an error about the medibuntu repository then it's their repo that has issues so we'll definitely need to report it to them.

---

### Post by jw5801 on 2007-11-19
Oh, and don't forget to add the GPG key, else apt-get will tell you the packages can't be verified. ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by kleo skywalker on 2007-11-19
If you have backed up your data AND are intimidated by complex solutions (I'm a newbie too and I would be), just do a fresh install.

---

### Post by jw5801 on 2007-11-19
> **kleo skywalker said:**
> If you have backed up your data AND are intimidated by complex solutions (I'm a newbie too and I would be), just do a fresh install.

Why on earth would that be necessary?! All he needs to do is delete a file, and append one line to another file and he'll get the result he was after. I guess it does look kinda complicated when I give the text file editing stuff as one commandline entry doesn't it? Ah well, the gpg key bit is copied straight from the medibuntu site, which is where the problem with the repository list started out from anyway!

---

### Post by Beaucephus on 2007-11-19
Reinstalling when problems arise guarantees you will forever be a noob.  Seek help and you will learn.  Nothing here is too complicated, you just have to discover one thing at a time.  It's a steep learning curve, but you get there fast.

---

### Post by Paul820 on 2007-11-19
> If you have backed up your data AND are intimidated by complex solutions (I'm a newbie too and I would be), just do a fresh install.
WOW :shock:

Don't be intimidated by it, if you take one instruction at a time it's actually very simple. The more challenging part is learning **what** each instruction does.]Do a bit of reading and learn about linux, as reinstalling every time you find something difficult is going to get you nowhere. Just the thought of reinstalling would make me want to learn.

---

### Post by jw5801 on 2007-11-19
> **Paul820 said:**
> WOW :shock:

Don't be intimidated by it, if you take one instruction at a time it's actually very simple. The more challenging part is learning **what** each instruction does.]Do a bit of reading and learn about linux, as reinstalling every time you find something difficult is going to get you nowhere. Just the thought of reinstalling would make me want to learn.

You don't even need to go looking for reading material, just ask the person who posted the command and we'll almost certainly give you a detailed explanation of what the command does!

---

### Post by kleo skywalker on 2007-11-20
If the person with the problem is indeed a complete newbie, it might be easier for her to learn one thing at a time, starting with something simple and non-scary. When you know stuff and have certain skills regarding a particular subject, it's easy to not know or forget how it is for someone who knows very little or doesn't have those skills (computer-related skills, knowledge and confidence are far less universal than many experienced people on this forum seem to believe).
Editing a file might seem like a breeze to some people,  but to many others it seems difficult. When I had just switched to Ubuntu, I was advised to do something similar and I had a hard time figuring out how, despite that things didn't go right. At a time when you're already grappling with something new and trying to get your computer working, there's only so much new stuff that you can take at once. If this person is in such a situation, why can she not go ahead and reinstall? Except that some people think she "should learn"? Moreover, many people just want to use their computer for some basic fun and work functions, and don't want to learn anything beyond that, and they shouldn't have to.
Also, I simply suggested a fresh install as one of many options qualified with conditions. I did not say that one should go reinstall every time one is faced with problems, but if one's at the beginning then it won't hurt. Once you're a little used to Ubuntu, and you have a clue about what things like software sources, repositories etc. mean, you can attempt to solve problems by doing things you haven't done before.

---

### Post by jw5801 on 2007-11-20
> **kleo skywalker said:**
> If the person with the problem is indeed a complete newbie, it might be easier for her to learn one thing at a time, starting with something simple and non-scary. When you know stuff and have certain skills regarding a particular subject, it's easy to not know or forget how it is for someone who knows very little or doesn't have those skills (computer-related skills, knowledge and confidence are far less universal than many experienced people on this forum seem to believe).
Editing a file might seem like a breeze to some people,  but to many others it seems difficult. When I had just switched to Ubuntu, I was advised to do something similar and I had a hard time figuring out how, despite that things didn't go right. At a time when you're already grappling with something new and trying to get your computer working, there's only so much new stuff that you can take at once. If this person is in such a situation, why can she not go ahead and reinstall? Except that some people think she "should learn"? Many people just want to use their computer for some basic fun and work functions, and don't want to learn anything beyond that, and they shouldn't have to.
Also, I simply suggested it as one of many options, and qualified it with conditions. I did not say that one should go reinstall every time one is faced with problems, but if one's at the beginning then it won't hurt. Once you're a little used to Ubuntu, you can attempt to solve problems by doing things you haven't done before.

For the record it would appear that the OP has solved their problem and moved on. *Without* reinstalling.

<rant>
Reinstalling is a last resort option that should never suggested as the easiest option for a fairly simple problem! If we had been debugging errors in Xorg that were preventing the OP from logging in graphically at all, then yes, reinstalling might be a viable option. But that wasn't the case, it was a fairly simple issue, and I gave 2 commands that only needed to be copied and pasted into a terminal and run to fix the problem, how is reinstalling more simple than that? Not even 2 minutes of typing, or at least an hour reinstalling and setting their system back up again? I don't mean to sound condescending but reinstalling is an absolute pain where the sun don't shine, and copying a command to a terminal, even if you're not sure what it does, has to be easier than that. Let's face it, even if I was the idiot posting a command to recursively delete the home directory without asking confirmation, copying that command would only result in the need for a reinstall anyway, so surely it's better to try to fix the problem first? I don't think people need to be told that they can reinstall and start over if something goes wrong, I'm pretty sure they already know that and they post here to try and avoid it, and maybe to learn something about their system!
</rant>

---

### Post by kleo skywalker on 2007-11-20
> **jw5801 said:**
> For the record it would appear that the OP has solved their problem and moved on. *Without* reinstalling.

<rant>
Reinstalling is a last resort option that should never suggested as the easiest option for a fairly simple problem! If we had been debugging errors in Xorg that were preventing the OP from logging in graphically at all, then yes, reinstalling might be a viable option. But that wasn't the case, it was a fairly simple issue, and I gave 2 commands that only needed to be copied and pasted into a terminal and run to fix the problem, how is reinstalling more simple than that? Not even 2 minutes of typing, or at least an hour reinstalling and setting their system back up again? I don't mean to sound condescending but reinstalling is an absolute pain where the sun don't shine, and copying a command to a terminal, even if you're not sure what it does, has to be easier than that. Let's face it, even if I was the idiot posting a command to recursively delete the home directory without asking confirmation, copying that command would only result in the need for a reinstall anyway, so surely it's better to try to fix the problem first? I don't think people need to be told that they can reinstall and start over if something goes wrong, I'm pretty sure they already know that and they post here to try and avoid it, and maybe to learn something about their system!
</rant>

If the problem has been solved, then good for the person who started this thread.
I'm sure you don't mean to sound condescending, many on this forum don't, but they end up sounding that way. Does it occur to you that there are people who don't know what "Terminal" means, how to access it, or what to do with it?
Or that not knowing this does NOT make a person an idiot?

---

### Post by jw5801 on 2007-11-20
> **kleo skywalker said:**
> If the problem has been solved, then good for the person who started this thread.
I'm sure you don't mean to sound condescending, many on this forum don't, but they end up sounding that way. Does it occur to you that there are people who don't know what "Terminal" means, how to access it, or what to do with it?
Or that not knowing this does NOT make a person an idiot?

I'm well aware that there are people who don't know what the terminal is or how to get to it! And of course I know that that doesn't make the person an idiot! I also know, however that all they need do to find out what it is and how to get to it, is to reply with "What is a terminal and how do I get one?" and I'll tell them. When I'm posting in this forum my assumed level of knowledge is that a person knows how to open a terminal, that's about it! Occasionally someone doesn't, they ask how, I tell them. I may post commands that look like confusing gibberish to the new user and return even more confusing gibberish that I ask them to reply with, but I only do that so I can assess the problem and post a (potentially equally confusing) fix. The reason we use the commandline for things like this is because it can be so easily copied and pasted. You also mention that some new users have trouble opening a file for editing with root permissions, this is why I post commands like "echo blah | sudo tee -a file" because that way all they need to do is copy the line and it will append whatever is necessary to the end of the file for them. You get two types of responses to this approach, one that will take the fix, be happy it works now and go on their merry way, and the other that will try to understand what the fix was, and how it worked, either by posting again asking me to explain the command, or by doing some research on their own.

This is off topic anyway, I'd still like to know why you think a complete reinstall easier than searching for a fix? If the user has just installed their system and encountered the error on first boot, then yeah, it might be viable to reinstall, but chances are they'll encounter the problem again! If they've done some configuration and had something break on them (in this case due to a bad link on the medibuntu site), it's probably easily fixable if you know what to look for, and chances are, the user doesn't want to have to redo all their configuration after a reinstall. Sorry to get my back up and sound a bit argumentative, but your initial post came across as if you were trying to say "don't take the above suggestion, instead reinstall, you'll be better off," which struck me as extremist and blatantly unnecessary. If the user can't open a terminal, ask, if they can't copy and paste, ask. Reinstalling is not going to help either of these things, and they were all that was necessary to follow my suggestion.

---

### Post by jaybombalous on 2007-11-20
> **kleo skywalker said:**
> If the problem has been solved, then good for the person who started this thread.
I'm sure you don't mean to sound condescending, many on this forum don't, but they end up sounding that way. Does it occur to you that there are people who don't know what "Terminal" means, how to access it, or what to do with it?
Or that not knowing this does NOT make a person an idiot?


if they don't know what a terminal is or can't find it then they may need more help then this forum can offer. We are not a fix all, dump all, problematic solution. We can only help those that need help and want help. its assumed u know what a computer is and general terminology used in computers. NOTE: that doesn't have to mean u know what a 'terminal' is, but you should know what a command line is and what u can type there. :)

re-installing is not a viable option when there is an easier solution, whether u feel its easier or not!

---

### Post by kleo skywalker on 2007-11-20
jw5801, I never suggested that a reinstall was an easier solution than searching for a fix in general. By the sound of deepblue80's posts, it seemed to me that she had just started out with Ubuntu, that is, just installed it. I remember the time when I had just installed Ubuntu and found it difficult to follow similar solutions - even if they only involved opening the terminal and running some seemingly simple commands. Keeping this in mind, I suggested a fresh install as one possible option. I'm sure you can see that if she had just installed Ubuntu, she would've probably made few, if any, changes to her computer that would be time consuming to redo on a reinstall. My point is this - instead of assuming that a beginner knows stuff, I assume that she doesn't. 
Say you're someone who's never installed an OS and use the computer for simple stuff like word processing, browsing the internet, listening to music etc. One day, you find out that there exists a thing called Ubuntu and decide to make the switch - not a small decision. You find out what Ubuntu is about and what it's like. You find out how to download, burn and install. You probably find out how to partition your hard disk. You find out how to get it doing the things you do - configure an internet connection for example. That is already a lot of new things you've learnt and remembered. Then you install, and find that something is wrong. You post on the forum, and get suggestions and advice from kind people who spare time and effort to solve your problem. Except, despite their best intentions, the solutions they suggest intimidate you a little. You think, "I'm confused, how do I go about this? What if I break something or make things worse?"
In this specific situation, is it a problem if there's a less intimidating solution available which you can choose to pick or not pick? Like a fresh install because you've already done it once? If things still don't work, of course you have the option attempting the other solutions offered.

And jaybombalous, whether you feel a solution is easier or not IS what matters. In context of what I've said above, the beginner isn't familiar with the actual difficulty of a task, so that is not as important as the perceived difficulty. Also, the terminal thing is an example to illustrate my larger point - that it isn't very fair to decide what someone "should" or "should not" know.

---

### Post by jw5801 on 2007-11-20
> **kleo skywalker said:**
> jw5801, I never suggested that a reinstall was an easier solution than searching for a fix in general. By the sound of deepblue80's posts, it seemed to me that she had just started out with Ubuntu, that is, just installed it. I remember the time when I had just installed Ubuntu and found it difficult to follow similar solutions - even if they only involved opening the terminal and running some seemingly simple commands. Keeping this in mind, I suggested a fresh install as one possible option. I'm sure you can see that if she had just installed Ubuntu, she would've probably made few, if any, changes to her computer that would be time consuming to redo on a reinstall. My point is this - instead of assuming that a beginner knows stuff, I assume that she doesn't. 
Say you're someone who's never installed an OS and use the computer for simple stuff like word processing, browsing the internet, listening to music etc. One day, you find out that there exists a thing called Ubuntu and decide to make the switch - not a small decision. You find out what Ubuntu is about and what it's like. You find out how to download, burn and install. You probably find out how to partition your hard disk. You find out how to get it doing the things you do - configure an internet connection for example. That is already a lot of new things you've learnt and remembered. Then you install, and find that something is wrong. You post on the forum, and get suggestions and advice from kind people who spare time and effort to solve your problem. Except, despite their best intentions, the solutions they suggest intimidate you a little. You think, "I'm confused, how do I go about this? What if I break something or make things worse?"
In this specific situation, is it a problem if there's a less intimidating solution available which you can choose to pick or not pick? Like a fresh install because you've already done it once? If things still don't work, of course you have the option attempting the other solutions offered.

And jaybombalous, whether you feel a solution is easier or not IS what matters. In context of what I've said above, the beginner isn't familiar with the actual difficulty of a task, so that is not as important as the perceived difficulty. Also, the terminal thing is an example to illustrate my larger point - that it isn't very fair to decide what someone "should" or "should not" know.

Fair enough, and I agree that things can appear to be intimidating, but I would also like to say that suggesting a reinstall can make my suggestion appear to be even more intimidating that would originally have been, it implies that you, another experienced user, feel that a reinstall would be much less dangerous than my much simpler (to the experienced eye, anyway) suggestion. I felt it would be much more constructive for the new user to ask and inquire about a command that they felt was intimidating (ie. face the fear), rather than just reinstall (running away from the fear).

Anyway, good to have a civil discussion! It very rarely happens on forums of any variety, so it's testament to the community that is Ubuntu!

---

### Post by kleo skywalker on 2007-11-20
> **jw5801 said:**
> Fair enough, and I agree that things can appear to be intimidating, but I would also like to say that suggesting a reinstall can make my suggestion appear to be even more intimidating that would originally have been, it implies that you, another experienced user, feel that a reinstall would be much less dangerous than my much simpler (to the experienced eye, anyway) suggestion.

I have to admit, that did not occur to me. 
And yes, if one wants to, it's good to explore commands. Just that sometimes too much new information means you can't make sense of most of it. That's really all I had in mind while giving that suggestion.
P.S.: And I'm far from an experienced user - the beans just mean I ask a lot of questions!

---

### Post by jw5801 on 2007-11-20
<pretend C>
if(questions&&((time&&research)||answers) {
    user = experienced;
}
</pretend C>

Translation: If a user has many questions and either receives answers or spends time finding the answers themselves, then they become experienced!

---

### Post by deepblue80 on 2007-12-02
> **jw5801 said:**
> For the record it would appear that the OP has solved their problem and moved on. *Without* reinstalling.

<rant>
Reinstalling is a last resort option that should never suggested as the easiest option for a fairly simple problem! If we had been debugging errors in Xorg that were preventing the OP from logging in graphically at all, then yes, reinstalling might be a viable option. But that wasn't the case, it was a fairly simple issue, and I gave 2 commands that only needed to be copied and pasted into a terminal and run to fix the problem, how is reinstalling more simple than that? Not even 2 minutes of typing, or at least an hour reinstalling and setting their system back up again? I don't mean to sound condescending but reinstalling is an absolute pain where the sun don't shine, and copying a command to a terminal, even if you're not sure what it does, has to be easier than that. Let's face it, even if I was the idiot posting a command to recursively delete the home directory without asking confirmation, copying that command would only result in the need for a reinstall anyway, so surely it's better to try to fix the problem first? I don't think people need to be told that they can reinstall and start over if something goes wrong, I'm pretty sure they already know that and they post here to try and avoid it, and maybe to learn something about their system!
</rant>

Hello
I have been away and just followed the instructions in your first few posts. the problem is now solved!! i can see it has led to a debate on here including a presumption on my gender! I just wanted to thank you for your help and let you know you solved my problem, now to update the system and move onto the new version 7.10!! :-)

---

