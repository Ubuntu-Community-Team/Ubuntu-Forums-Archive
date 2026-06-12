---
title: "Please help me install a piece of software."
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Swerve1000 on 2007-02-23
Hi,

As I type this I have Ubuntu 6.06 installed as a virtual machine via VMware workstation.

I want to install the VMware tools but have never installed any software on Linux before.

Coud someone possibly talk me through the installtion. There are two files on my Ubuntu desktop, an .rpm file and a .tar.gz file.

Could someone talk me through the installation of this software? 

I am able to do this and give instant feedback as to what the screen is saying as it is up and running now.

Many thanks.

:)

---

### Post by linux_kid on 2007-02-23
#1 Were any *.deb files avaliable to be used for vmtools?
#2 So you're in some other os with Ubuntu as a virtual machine?

---

### Post by Swerve1000 on 2007-02-23
1 , no the only two file I see are the two I listed

2) yes, host is xp pro, ubuntu is running as the guest

---

### Post by linux_kid on 2007-02-23
Ok, extract the tarball and look for a README file inside, possibly uploading it here as an attached text file.

We are going to forget about the .rpm because debian based distro's (such as Ubuntu) don't support this type of file.

---

### Post by Swerve1000 on 2007-02-23
How do I extract a tarbell (the tar.gz file i presume)?

I'm complete noob at linux.

---

### Post by linux_kid on 2007-02-23
Ok, sorry if I confused you. :rolleyes: lol

Simply click on the .tar.gz file to pop up a window that will extract it for you.  A new folder will appear on your desktop

Click on that folder and look for a file named "README"

Copy the contents and paste it here and I will tell you the next step.

---

### Post by Zafrusteria on 2007-02-23
After clicking on the menu option "install VM tools" You should see an icon on your desktop for vmware tools.
double click on this to open your file manager.
Right click on the tar.gz file and select Extract from the menu
Change the directory mentioned in the list box to /tmp (seems as good a place as anywhere:-)
When the extraction has finished, open a terminal window and "cd /tmp" or where ever you extracted the tar.gz to.
You should see a directory called vmware-tools-distrib, cd into that directory.

then you need to run the install script 

sudo ./vmware-install.pl

follow the prompts, when I did this I just accepted all the defaults and after  a while it was all done.
It's worth rebooting at this point, ( I don't know how to restart every thing from the command line :-)

to be tidy you can remove the  extracted files from /tmp after the reboot.

Hope that helps.

---

### Post by Swerve1000 on 2007-02-23
[IMG]http://i25.photobucket.com/albums/c77/Swerve1000/1-3.jpg[/IMG]

that is what is there.

Thanks for your help! I really do appreiciate it!

---

### Post by linux_kid on 2007-02-23
Swerve1000, are the tools installed properly?

---

### Post by Swerve1000 on 2007-02-23
No mate, I'm just at the stage in the picture above. :(

---

### Post by Swerve1000 on 2007-02-23
Can anyone tell me what I should do next to install this software?

I just want to learn how to install it.


:)


The current stage

[IMG]http://i25.photobucket.com/albums/c77/Swerve1000/1-3.jpg[/IMG]

---

### Post by useResa on 2007-02-23
> **Swerve1000 said:**
> Can anyone tell me what I should do next to install this software?
 
I have posted a picture above of where I am right now, I just want to learn how to install it.
 
 
:)
 
 
The current stage
 
[IMG]http://i25.photobucket.com/albums/c77/Swerve1000/1-3.jpg[/IMG]
 
1. Change the location as indicated above into /tmp/vmware-tools-distrib/.
2. Click the Extract button in the menu
3. Follow the instructions as given by Zafrusteria in post [#7](http://www.ubuntuforums.org/showpost.php?p=2201523&postcount=7).
 
Good luck

---

### Post by Swerve1000 on 2007-02-23
Thanks, I changed the location as suggested and pressed extract and then this window appeared.

[IMG]http://i25.photobucket.com/albums/c77/Swerve1000/2-3.jpg[/IMG]

What should I select? Do I need to change any of the settings? Should I just select the 'Extract' option?

Many thanks!

---

### Post by Repent on 2007-02-23
Click on Extract, and go back to post number 7.

---

### Post by Swerve1000 on 2007-02-23
Ok, I clicked on extract and got the following message appear:-

[IMG]http://i25.photobucket.com/albums/c77/Swerve1000/3-3.jpg[/IMG]

Is this to do with uBuntu being hosted on vmware? 

I don't know what to do.

---

### Post by linux_kid on 2007-02-23
Click the extract button and extract it to /tmp as stated before

---

### Post by linux_kid on 2007-02-23
> Ok, I clicked on extract and got the following message appear:-



Is this to do with uBuntu being hosted on vmware?

I don't know what to do.

No, you selected to extract it to a CD, change the directory to extract to, to somthing like /tmp

---

### Post by Repent on 2007-02-23
Oh my bad, I should have noticed that sorry.

---

### Post by linux_kid on 2007-02-23
Where did you extract it to?
Note: Just extracting to the desktop should be fine.

---

### Post by Repent on 2007-02-23
Oh my bad, I should have noticed that sorry.  Extract it into  /tmp/vmware-tools-distrib/   
 as per useResa


Wow how did that happen ?

---

### Post by Swerve1000 on 2007-02-23
What do you mean by 'like' /tmp.

I do not understand.

I changed the location as told ( at the top in the part similar to an address bar ) to :-

/tmp/vmware-tools-distrib/

As I have done in the picture here-

[IMG]http://i25.photobucket.com/albums/c77/Swerve1000/5-3.jpg[/IMG]

I then clicked 'extract'

[IMG]http://i25.photobucket.com/albums/c77/Swerve1000/6-3.jpg[/IMG]

and the screen above appears.

These settings do not work.

Do I need to change the settings in the 'Extract' window shown above aswell and NOT press 'Extract' button straight away? Do some of the settings in the above window need to be changed?

---

### Post by Swerve1000 on 2007-02-23
OK, so it DOES need to be changed.

What and how should I do?

The options below are available:-

[IMG]http://i25.photobucket.com/albums/c77/Swerve1000/7-3.jpg[/IMG]

---

### Post by linux_kid on 2007-02-23
Yes, that's what needs to be changed

---

### Post by Swerve1000 on 2007-02-23
Thanks, how? :( 

Which option and what should I enter?

---

### Post by Swerve1000 on 2007-02-23
Please guys, I've been trying to install this for over 2 hours now. Just to install 1 piece of software.

I've explained everything clearly and posted accompanying screen shots.

What should I select on the picture above?

---

### Post by Swerve1000 on 2007-02-23
OK, so I just guessed, rightly or wrongly.:( 

I chose 'Desktop'.

I now get this screen:-
[IMG]http://i25.photobucket.com/albums/c77/Swerve1000/8-1.jpg[/IMG]

Is there anyone on the forum who knows how to install software on Ubuntu?

I need some help please.

What should I do now?

I have provided as much information as I can all along.

---

### Post by Maestro23 on 2007-02-23
> **Swerve1000 said:**
> OK, so I just guessed, rightly or wrongly.:( 

I chose 'Desktop'.

I now get this screen:-
[IMG]http://i25.photobucket.com/albums/c77/Swerve1000/8-1.jpg[/IMG]

Is there anyone on the forum who knows how to install software on Ubuntu?

I need some help please.

What should I do now?

I have provided as much information as I can all along.

Yes, there are plenty of people on the forums who know how to install software.  Looks like you have been getting help. Did you take a look at the installation instructions over at the Vmware site by chance.

I don't know what version you are running, but here is the instructions for 5.5
What version of VmTools are you trying to install?  

[http://www.vmware.com/support/ws55/doc/ws_newguest_tools_linux.html](http://www.vmware.com/support/ws55/doc/ws_newguest_tools_linux.html)

---

### Post by Swerve1000 on 2007-02-23
Many thanks but I am trying to learn how to install software on Ubuntu. 

I am hoping that by learning to install this piece of software I will not have to come back here again and ask again for help with another piece of software I will want to install.

Surley it's pretty much the same every time. 

I just want to know what Icon or whatever I should press to install it from the picture above.

The help I recieved earlier was incorrect and that's why I am still here and dispite my asking "OK, so it DOES need to be changed. What and how should I do that?"

I recieve responses like "Yes, that's what needs to be changed". 

I stated that in my question.

This is why I am still here.

This is not fare.  I have posted screen shots on nearly all of my posts and explained each question as clearly as I can in a structured way.

I am here, with uBuntu running and i could of achieved this many haours ago with some help from someone who would be kind enough to just spare me 5 minutes of their time.  I said in the first post I will give immeadiate feedback.

I was hoping to create a thread which would help other people in the future but it just getting filled by responses which have already bee answered or don't move the topic forward.

It's 3 pages now, this is not fare.

---

### Post by Swerve1000 on 2007-02-23
ttt

---

### Post by Maestro23 on 2007-02-23
> **Swerve1000 said:**
> ttt

Why don't you take 15 minutes and read this and take things step-by-step.

How-To: Vmware/Tools: [https://help.ubuntu.com/community/VMware/Tools?highlight=%28vmware%29](https://help.ubuntu.com/community/VMware/Tools?highlight=%28vmware%29)

There are many Vmware/Tools threads on the forums, and the above [COLOR="Red"]How-To[/COLOR] has helped many users.

Good luck.

---

### Post by Swerve1000 on 2007-02-23
> **Maestro23 said:**
> Why don't you take 15 minutes and read this and take things step-by-step.

How-To: Vmware/Tools: [https://help.ubuntu.com/community/VMware/Tools?highlight=%28vmware%29](https://help.ubuntu.com/community/VMware/Tools?highlight=%28vmware%29)

There are many Vmware/Tools threads on the forums, and the above [COLOR="Red"]How-To[/COLOR] has helped many users.

Good luck.


Oh forget it. 

I've sat here for 3 hours now (it's currently 1.40 am here now) with it running and ALL I WANTED was for someone to say 'click that and enter this' and this thread, with all the screen shots and basic, standard english, would of provided new users to Ubuntu a great tutorial to follow.  It would of taken 15 minutes, max.

But no, all I have recieved is posts from people who have failed to read my simple question's or said 'look at this link' when the link is a completely different method of installation as I have been trying to do.

---

### Post by Swerve1000 on 2007-02-23
You may be suprised to know that instructions such as "NOTE: linux-headers-uname -r is not required on a default build as these headers already exist. They are listed here in case you have made kernel modifications."

don't make sense to everyone. Sometimes people require some extra help.

---

### Post by linux_kid on 2007-02-23
Swerve1000, sorry, but I'm going to request you [read this post about a fisherman]("http://www.ubuntuforums.org/showpost.php?p=1488521&postcount=1"), sit down, relax, sleep, wake up, go do your day stuff, come back to your PC, and calmly fix this.

---

### Post by Zafrusteria on 2007-02-25
Hi Swerve1000

I did or thought I gave you step by step instructions. Which bit did you get stuck on?

But like all the other guys have said, you do need to read stuff to learn. I loved the fishing thing shame I hate fishing to much just stilling around waiting :-)

one thing you seemed to have missed is that you need to run the tools from a "command prompt" (terminal, xterm, etc) or you will not see the questions :-)

---

