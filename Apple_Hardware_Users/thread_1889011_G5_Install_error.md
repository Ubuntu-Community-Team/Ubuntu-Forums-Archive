---
title: "G5 Install error"
date: 2011-11-30
forum: Apple Hardware Users
---

### Post by Trisket on 2011-11-30
I'm trying to install 10.04 on my mac G5, the ppc iso is good, and the computer boots into live mode. When i try to install it, it goes through the normal process up until you select the keyboard set up, upon hitting "forward" after making your selection, the computer does nothing but the mouse indicates it is thinking. I believe this is the portion of the setup when it accesses the hdd....also the hdd is wiped....not sure what to do here but any help would be appreciated, I have 12 g5's to install this on..

---

### Post by pauljwells on 2011-11-30
I've found it much more reliable to install using the alternate installer isos. 11.04 was the last one that worked for me. Others have had better and worse experiences. G5s are no longer well supported by any linux distro... :-(

If you just need to get a relatively modern OS onto these machines I'd strongly recommend mintppc - it is at least supported by a small but knowledgeable and keen community. I'm thinking that's where I'll end up now.

---

### Post by rsavage on 2011-12-01
> **pauljwells said:**
> I've found it much more reliable to install using the alternate installer isos. 11.04 was the last one that worked for me. Others have had better and worse experiences. G5s are no longer well supported by any linux distro... :-(
 
If you just need to get a relatively modern OS onto these machines I'd strongly recommend mintppc - it is at least supported by a small but knowledgeable and keen community. I'm thinking that's where I'll end up now.
 
I can't believe you just said that. MintPPC is just debian, but with the LXDE interface and the Mint theme. A G5 is capable of so much more than LXDE.
 
MintPPC 9 is based on debian stable so unsuprisingly it is quite stable. However, in order to achieve that stability the various packages spend many months in testing and it can end up that the packages in stable are like two years old or something. Because a lot of improvements have not filtered down yet, some things like the autoconfiguring of X do not work so well. So the MintPPC9 forum is filled with people with broken screens requiring an xorg.conf. Also, if you use a modern plug n play device it may not work so well.
 
These are the reasons why I assume linuxopjemac (because it is only him really behind MintPPC) has used debian testing for MintPPC 11. You could argue that it's 'stability' is now on a par with Ubuntu 11.10 (and MintPPC 9 is on a par with Ubuntu 10.04).
 
I can't argue with the MintPPC forum being a friendly place and many of their members are very vocal on other mac sites. That (and the hype over the original Mint) is why I assume they appear to be attracting a healthy number of new members. But, the vast majority of technical questions are still answered by linuxopjemac who used to post on this forum (and is very welcome to again). You don't get discussions on how to compile packages for example. And of course, with Ubuntu, if it is a question that doesn't relate to PPC hardware directly you can always post your question on one of the other sub forums so your question will be seen by hundreds/thousands.
 
I don't know what the documentation for MintPPC is like (it is behind closed doors), but I think you would be hard to beat the present Ubuntu documentation for PPC 11.04 and 11.10 (which also covers 10.04).
 
I'm not knocking MintPPC. I think you should try as many distributions as possible because the only opinion that counts is your own. I'm just saying it is not time yet to throw in the towel with ubuntu.
 
@Trisket I'm assuming you chose the 64bit version? As pauljwells says, try the alternate install.

---

### Post by linuxopjemac on 2011-12-01
Of course everybody is free to choose whatever distribution he/she wants on his/her Mac. Ubuntu is a great operating system and it looks beautiful. Personally, I am more interested in speed and ease of installation and that everything works out of the box.

Another point that I like to make is that I ported not only the Linux Mint LXDE packages, but also the Linux Mint main edition's packages, which are aimed at GNOME. A person who does not like LXDE can simply login into a GNOME session and he then ends up in Linux Mint ported to PPC. So both LXDE and GNOME sessions are possible. Not everyone is aware of that possibility. The default will always be LXDE as that is the faster desktop manager which I prefer and which is more suitable for the slower processors out there.

As I said, the great thing about Linux is that it comes in so many flavours. There is choice for everyone. We should not be telling that one is better than the other, it's a personal taste. We should also not try to stop people from trying out those other flavours. Freedom is king, that is what Linux is all about.

Edit: The GNOME session only works in MintPPC 9 so far. I did not make it work in 11 yet...

---

### Post by rsavage on 2011-12-01
@linuxopjemac
 
I think we are singing from the same hymn sheet on this. One thing that really really annoys me about Linux is the squabbling between distros or the in-fighting in a distro (e.g. the endless unity vs. non-unity debate). It is likely to put new people off rather than attract them to a certain distro. Much of what is written is such rubbish too! I shied away from using xubuntu for ages due to the bad reports that I had read, but in fact, it is superb (IMHO)! I concluded (and is the message I have been trying to put across for a bit now is) that you don&#8217;t know what a distro is like until you personally have tried it.
 
With that in mind, I apologise if I have mis-represented MintPPC in the above post. Your website makes no mention of Gnome I think? I did know that it was possible to switch to a gnome session (in v9) but I wasn&#8217;t aware that it was so well integrated (in v9).
 
I do admire your dedication to MintPPC/linux. I don&#8217;t think people appreciate when they ask questions how time consuming it is to answer them. It annoys me so much when I answer a question and then receive no feedback (or worse the person is rude back). This has happened so many times now that I&#8217;m starting to be selective about the posts I answer. Besides, I don&#8217;t have the actual time to answer everything. And why should I? Ubuntu is community supported not rsavage supported!! 
 
The &#8216;lubuntu&#8217; instructions are in a very good state right now I think. There are enough links to them across the forum that you can&#8217;t miss them. So my policy for the moment (due to time issues) is if you can&#8217;t be bothered to read the documentation then I can&#8217;t be bothered to answer your question! If somebody posts a problem with the documentation or doesn&#8217;t understand something on them then I&#8217;ll be more than happy to help out. 
 
Undoubtedly, for a newbie MintPPC is probably easier to install than 11.10. However, it annoys me so much when people suggest MintPPC as a sweep all solution to installing Ubuntu. Particularly if the problem is something trivial like configuring X that they are going to also run into when they install Mint. It is bad advice.
 
I&#8217;m not sure I am putting this across well here (or in the past on other posts). It is difficult to defend ubuntu without sounding like you are attacking the other distro that could be MintPPC, debian etc. 
 
Getting back to the G5s, I think pauljwells has been a bit misleading. 11.10 has been reported to have been installed on a G5 (the iMac G5 for example). Perhaps you could try it out on your new iMac G5? Btw, I couldn&#8217;t help but notice another thread in your &#8220;off-topic&#8221; area&#8230;.oh well&#8230;...did you try and find out why it was slow? I bet it was the udev bug which is well discussed&#8230;&#8230; If not it could be something worth exploring.
 
 
@pauljwells
 
If ubuntu on PPC is to continue then it has got to overcome these three problems I think:
 
The main problem that I can see is the lack of people willing to test the development versions. When I (eventually) get my PPC machine backup I&#8217;m going to switch to 12.04. That version of ubuntu should have 5 years support which should see most PPC machines out. 
 
The second biggest problem is people have given up reporting bugs. Things are not going to get fixed if they are not reported. People don&#8216;t even post the problem on the ubuntuforums, but you read about them on some other random forum.
 
The third problem is most of the people who do post on the apple ubuntuforum are only asking questions and do not take the time to answer somebody else&#8217;s question. You are missing out a lot if you don&#8217;t read other people&#8217;s posts. A lot of people don&#8217;t even do a search before they post.
 
The common theme is there needs to be more active PPC people and you don&#8217;t need to be an expert to be a valuable member of the community. 
 
The solution to better PPC Ubuntu is to attract more people to Ubuntu rather than drive them needlessly away.

---

### Post by B_Free on 2011-12-01
Check this [https://lists.launchpad.net/lubuntu-desktop/msg05173.html](https://lists.launchpad.net/lubuntu-desktop/msg05173.html)

---

### Post by rsavage on 2011-12-01
> **B_Free said:**
> Check this [https://lists.launchpad.net/lubuntu-desktop/msg05173.html](https://lists.launchpad.net/lubuntu-desktop/msg05173.html)
 
So? Sorry, it's late here and I'm missing the point you are trying to raise with that link.  
 
@Trisket
 
Sorry we've rather hijacked your thread! Are all your G5s the same model? Once you get installed and updated on one it maybe easier/quicker to clone the drive onto the others. Just an idea.

---

### Post by B_Free on 2011-12-02
He or she would like to get involved, help the PPC community. Isn't that what you were talking about?

---

### Post by rsavage on 2011-12-03
Then this link [https://lists.launchpad.net/lubuntu-desktop/msg05460.html](https://lists.launchpad.net/lubuntu-desktop/msg05460.html) and the follow-up messages would have been better.

---

