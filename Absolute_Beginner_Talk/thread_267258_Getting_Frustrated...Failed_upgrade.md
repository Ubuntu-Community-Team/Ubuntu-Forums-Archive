---
title: "Getting Frustrated...Failed upgrade"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by snteran on 2006-09-28
I'm not sure if this is the correct location for this thread but initially I had posted on a thread for  “Howto: Fglrx 8.26.18 Driver Install” and I was trying to increase my video to at least 1024 X 768 and I was referred to a link that first had you upgrade to the new Dapper.  Well I now do not have a screen, as soon as I login I get a black screen.  I can't believe it is so hard to just get a better screen resolution.  I'm getting a bit frustrated about something that would be so easy in Windows.  I'm trying to learn Linux because I think it would be a great system to teach my kids, but I'm really struggling myself.  Any help, advice would be great.  And sorry to be so down, but I'm just amazed at how hard it has been to accomplish such an easy task, or so I thought.
Additionally, I did read a post that I needed to edit my source.list but it is a read only and I can not edit the file.  I was told that I needed to be logged in under sudo, but not sure how that is done.  I tried using username of sudo, but that did not work.  ](*,)

---

### Post by petri on 2006-09-28
fglrx-drivers? So you have ATI? And which one of them? ATI is the real problem here not Linux. I know I have ATI too.

Which howto are you using anyway? I used this one [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) and there Method 2. My problem was I have an older ATI and they just stopped supporting it but I found the older drivers at their site [https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300) Mine is Radeon 8500.

If you don't know which graphics chips you got paste this in terminal ```
lspci
``` and paste the result here.

---

### Post by Monkus on 2006-09-28
Hi, I'm with you in the "frustrated with my resolution problems" room. I can however tell you about sudo and getting to your sources.list. Here is the deal. 

When you open up the terminal, type sudo (that will give you root or administrative access). 

so type this

sudo gedit /etc/apt/sources.list

sudo give you root access
gedit is the text editor you want to use
/etc/apt/sources.list is where your sources list is located so I knows what to open with gedit. 

I hope that helps.
 
Ubuntu to you!!:)

---

### Post by snteran on 2006-09-28
Thanks for the quick answers.  I'll find out tonight the ati card and post here.  I really appreciate the sudo help.  I'm stoked to try that tonight.  Although I might have to start from scratch if I can't get my screen up.  Which won't be that big of a deal.

---

