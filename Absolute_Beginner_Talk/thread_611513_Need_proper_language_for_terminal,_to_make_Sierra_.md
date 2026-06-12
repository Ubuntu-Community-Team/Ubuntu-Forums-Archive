---
title: "Need proper language for terminal, to make Sierra 875u work"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by CD4liberty on 2007-11-13
Can anyone translate this link [http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=607](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=607) so that I can type it into terminal and Ubuntu Feisty will understand the commands.

I've got the tar file and the zip file, but can't get it to go where the Sierra says it should go. I activated the aircard in Windows 2000, so I thought it would just work when I plugged it into my laptop that runs only Unbuntu.

Thanks.

---

### Post by SpiritIsReality on 2007-11-13
howdy
Do you know where your files are? Are they on the Desktop? or do we have to find them.
edit: of course you know, you're trying to move them.
 at the top of the screen, click on Applications > Accessories > Terminal , then type at the command prompt
cd Desktop
then tap the enter key. , then type 
ls -la 
then hit the enter key (after each command is typed in and looks good to you, you "enter" it, or it's called "run" the command, by pressing the enter key. please copy and paste the results of the ls -la command, here.
trails

---

### Post by SpiritIsReality on 2007-11-13
howdy
What you're lookin' for is right here, at the heading of Source Package (.tar, .tar.gz, .tgz, .tar.bz, ...) [http://monkeyblog.org/ubuntu/installing/#installing_with_terminal](http://monkeyblog.org/ubuntu/installing/#installing_with_terminal)
post back and ask for more help when/if you need it. If I'm not here, there be others.
trails

---

### Post by CD4liberty on 2007-11-13
> **SpiritIsReality said:**
> howdy
Do you know where your files are? Are they on the Desktop? or do we have to find them.
edit: of course you know, you're trying to move them.
 at the top of the screen, click on Applications > Accessories > Terminal , then type at the command prompt
cd Desktop
then tap the enter key. , then type 
ls -la 
then hit the enter key (after each command is typed in and looks good to you, you "enter" it, or it's called "run" the command, by pressing the enter key. please copy and paste the results of the ls -la command, here.
trails

It took a while for me to get there, but here's the results 

chuck@brownbear:~/Desktop$ ls -la
total 20
drwxr-xr-x  2 chuck chuck 4096 2007-11-12 12:55 .
drwxr-xr-x 38 chuck chuck 4096 2007-11-13 12:42 ..
-rwx------  1 chuck chuck 1425 2007-11-11 20:11 ppp-scripts.tar.gz
-rwx------  1 chuck chuck 5811 2007-11-11 20:09 sierra.v.1.0.6b.zip
chuck@brownbear:~/Desktop$

---

### Post by SpiritIsReality on 2007-11-13
howdy
when you post results of the command line, and you are on the post reply page, if you scroll down the page, there's a box Disable Smileys, put a check in there before hitting the 
Submit Reply or else the markings like : ( without the space become :( .Rats, I thought that would be a sad face.
try this : ) without the spaces and you get :) OH!! I checked the box!!doh! When you are at the Post Reply page, and click the more at the bottom of the faces on the right hand side of your post window that you type in, you will see what I mean in the window that opens.
So according to what it says at [http://monkeyblog.org/ubuntu/install..._with_terminal](http://monkeyblog.org/ubuntu/install..._with_terminal) what do we do next? If you don't know,just ask a question, like : no I don't know what to do next show me.(Take all the time you want, to read what it says there. even if it's a couple of days. I'm in no hurry. and I'm not going anywhere that I can't get back from. hopefully!) If I don't know how, which is bound to happen more often than not, we'll have to decide who's going to post a question where, to hopefully find out the answer from some kind user. I love teamwork around the buffalo corral when you run a couple hundred thru in a day or so, there's not a lot of time to .... chew the fat, and shoot the sh##. sometimes they get turned around so you end up shooting the fat and spitting. You have to keep your mouth shut
around the squeeze, but it's not always possible. You have to call out the number of the ear tags,..tell everyone your job is done,..like that...
 If you right click the monkeyblog link here, and choose open in another tab, then at the top of this window, you can click back and forth between here and there.
when you get back to this page, at the top left of firefox, there's a bent arrow, well a circle arrow. click that and the page gets refreshed so you can see if there's anybody else posting.? Cause If I get held up in town or whatever, somebody else will hopefully grab hold of the reins and steer this thread to where it ought to go. You gettin your op (opening post) answered.
trails

*** the link in post # 2 is working. the one in this post is 4fr'broke I copied and pasted an abbreviated link from the post #3. That does not work. In the editable text, it looks like this [http://monkeyblog.org/ubuntu/install..._with_terminal](http://monkeyblog.org/ubuntu/install..._with_terminal) . That won't go anywhere.
It should look like this [ht tp://monkeyblog.org/ubuntu/installing/#installing_with_terminal](ht tp://monkeyblog.org/ubuntu/installing/#installing_with_terminal) without the space in http
4fr broke. broke is well, it won't work. 4 f r is, well, say the number 4 , the letter f, and the letter r, 4 f r to somebody 3 or 4 times and ask them what it was you just said. 4fr. Do you know what fr's are 4? they are 4 the bull. haha! rancher joke. fr sounds a little like heifer without the h being pronounced too much.

---

### Post by CD4liberty on 2007-11-19
After 5 well deserved days hunting the wily whitetail (no results there as of yet, I've passed on smaller does, and was hoping for something with about 8 or 10 points), I've got some time to work with my laptop (I'm posting using the desktop using windoze and will then be turning around to do as instructed on the laptop).

Well, after reading that Ubuntu 7.10 would intentify and properly do what ever, with the Sierra card, I've got my laptop back to where it was before the OS Ubuntu 7.10 crashed the computer. I'm back with Feisty, and current with updates. But, I still can't figure out how to get the zip and tar file where they belong (i'm not even sure where they should go, it says the files should be located at /usr/src/linux, but I've got four different linus 's there), or to do whatever it is that they do (which is, obivously, run the card).

Is there anyone present, that might be able to help.

---

### Post by CD4liberty on 2007-11-23
Can anybody, with the knowledge, spare a few minutes to help me get this Sierra card software installed?

---

