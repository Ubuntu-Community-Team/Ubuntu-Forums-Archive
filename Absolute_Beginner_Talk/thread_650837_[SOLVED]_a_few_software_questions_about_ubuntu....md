---
title: "[SOLVED] a few software questions about ubuntu..."
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by swishthetoad on 2007-12-26
alright to give a little background about my situation...
i have always been a windows girl (although i didn't really like it much) i didn't really know something else existed.  my dad always talked about linux but it seems like an os that only computer geeks use.  i know essentially NO programming language...i have never manually ran or installed a program until now. 

so...a couple weeks ago a close friend switched to ubuntu and raved about it nonstop.  saying how simple it was, never crashed (unlike the system i was previously using - vista), and was remarkably simple.  
unfortunately i am having some hard times and want to ask some basic questions that can help me further understand ubuntu (gutsy).  i just bought my computer from tigerdirect ([here]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3402799&CatId=2510")), but don't know a whole lot about that either...*le sigh

here it goes

1.  how do i install programs/games (after i've downloaded them) in the terminal client? is there a basic programming language i need to learn on some hidden page somewhere...?
or maybe a tutorial?

2.  on windows they had a very good wifi roaming capabilities. it would just naturally pick up whatever wireless signal was around and i didn't need the name of it.  is there anything similar to that on linux?  i installed wifi-radar but i'm having problems figuring out how to run it properly.  when i run it upon booting up, it stays blank and does nothing. there is no button for me to push that says reload or scan....any ideas? 

3.  what are repositories? in human language please. 

4. am i just a fish out of water here and should i just give up now?  because i don't really want to.  i like the fact that this operating system is open source, along with the software supplied in the ubuntu package (open office, gimp, pidgen, extensive games). 

5. everytime my computer idles it asks me to put my password in before accessing the desktop but then it wigs out and get's stuck on a black screen with a bunch of error messages until i have to manually (ouch) restart it...any ideas why? 


hope i supplied enough information. thanks for reading through all that.

---

### Post by chessercizes on 2007-12-26
Heya!! glad you joined us here =)

1) downloading and installing is mostly one step!! what you do is go through add/remove or synaptic package manager, search for what you want, and hit install, and it'll be installed! Then you can just go through the menu and access it. To install stuff by terminal you would do something to the effect of:
```
sudo aptitude install *packagename*
```
this only really works if you know exactly the name of what you want. Its much easier to go through synaptic or add/remove.

2) i'm super sry, can't help you here =/. don't own a laptop, so dunno at all.

3) repositories is basically a place with a bunch of software that you can download and install. it's not a word to be scared of at all.

4) no way! you definately should NOT quit. stick it out, you'll be thankful you did once you start to understand stuff. I started off as a noob (still am, actually =/) and it was hard starting. but once you get going, its really really fun.

5) hmm, thats weird =/. does it get stuck at like a screensaver?

hope this helps

---

### Post by wormser on 2007-12-26
1.  Always install from the repositories first.  Its not a programming language but a bunch of commands.  The shell (terminal) is like the command prompt in XP.  Read this [whole page]("http://monkeyblog.org/ubuntu/installing/") and you will learn a lot about installing.

2. You never said which version of Ubuntu you are running. In Ubuntu there is an icon for networking by the clock.  Works like XP.

3. Repositories is like a library.  Its a place where installable software is stored on the net.  All the software is safe and certified to work with Ubuntu.

4. Don't give up.  I actually believe Linux is easier than XP.  Everything is more logical and more thought out.  This forum will help you with any questions.

5. I am not sure what is going on with out more details.  Start a new post with the error message, version of Ubuntu and details of what causes it.  There probably is a fix.  .

---

### Post by overdrank on 2007-12-26
4. am i just a fish out of water here and should i just give up now? because i don't really want to. i like the fact that this operating system is open source, along with the software supplied in the ubuntu package (open office, gimp, pidgen, extensive games).
If you ask that question the I think you should. 
[http://ubuntuforums.org/showthread.php?t=63315](http://ubuntuforums.org/showthread.php?t=63315)

---

### Post by Sef on 2007-12-26
> 1. how do i install programs/games (after i've downloaded them) in the terminal client? is there a basic programming language i need to learn on some hidden page somewhere...?
or maybe a tutorial?

Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

> 
2. on windows they had a very good wifi roaming capabilities. it would just naturally pick up whatever wireless signal was around and i didn't need the name of it. is there anything similar to that on linux? i installed wifi-radar but i'm having problems figuring out how to run it properly. when i run it upon booting up, it stays blank and does nothing. there is no button for me to push that says reload or scan....any ideas?[QUOTE]

What is your wireless card?  Hardware in GNU/Linux can work any where from OOTB (Out of the Box) to Not at All.  If we know what kind of wireless card you have then we could give you some help.  Please start a new thread for that problem.   (Always start a new thread for a problem.  If you have more than one problem in a thread, then one or more of the problems can be missed.)

3. [QUOTE]what are repositories? in human language please.

Repositories are the place where you download software from for Ubuntu.  From [Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu"): There are for parts of the repositories:  The Ubuntu software repository is organised into four "components", on the basis of the level of support Ubuntu can offer them, and whether or not they comply with Ubuntu's [WWW] Free Software Philosophy. The components are called Main (officially supported software), Restricted (supported software that is not available under a completely free license), Universe (community-maintained, i.e. not officially supported software) and Multiverse (software that is "not free").[/QUOTE]

4. > am i just a fish out of water here and should i just give up now? because i don't really want to. i like the fact that this operating system is open source, along with the software supplied in the ubuntu package (open office, gimp, pidgen, extensive games).

No, learning something new takes some time and patience.  Please ask any questions that you need to.

5. > everytime my computer idles it asks me to put my password in before accessing the desktop but then it wigs out and get's stuck on a black screen with a bunch of error messages until i have to manually (ouch) restart it...any ideas why?


Check System > Preferences > Screen Saver > Lock Saver When Saver is active.  (It's at the bottom.)  If it is checked, then uncheck it.  If it is not checked, then could you post the error messages in a new thread.

---

