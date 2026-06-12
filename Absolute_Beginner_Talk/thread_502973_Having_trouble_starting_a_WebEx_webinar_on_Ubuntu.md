---
title: "Having trouble starting a WebEx webinar on Ubuntu"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Cold-Gin on 2007-07-17
Hi. I am having trouble starting a Jboss WebEx webinar while running FireFox. After I login to the web page, I get a WebEx start up screen that says "Playback in progress", but then I receive the following error:

Load /home/<my profile>/.webex/atsbrecply.so failed?random=3562077310

The URL for the error page with this message is:

[https://jboss.webex.com/cmp0304l/webcomponents/jsp/docshow/gpcerror.jsp?siteurl=jboss&ErrorType=1&ErrorMsg=Load+%2fhome%2fbrendan%2f.webex%2fatsbrecply.so+failed%3frandom%3d3562077310](https://jboss.webex.com/cmp0304l/webcomponents/jsp/docshow/gpcerror.jsp?siteurl=jboss&ErrorType=1&ErrorMsg=Load+%2fhome%2fbrendan%2f.webex%2fatsbrecply.so+failed%3frandom%3d3562077310)

Prior to starting the webinar, I needed to create a symbolic link (under the firefox plugin directory) to the JRE that I have installed, which is version 1.5. After I did that, the WebEx session would start, but then I received the error described.

I read a few other posts about people not being able to run a WebEx session properly, but I didn't see anybody post this specific error.

I am running Ubuntu linux 7.04 (Feisty). Any help would be greatly appreciated. 

Thank you.

---

### Post by VoiceOvGod on 2007-07-19
Ubuntu isn't supported by WebEx.... 

I'm hoping that will change eventually.

---

### Post by BoxDog on 2007-08-14
Hi everybody

I am a WebEx employee and was actually referred to this page by a customer who uses Debian.  I just wanted to let you all know that WebEx will be supporting Ubuntu Linux 6.10 and 7.04 as of our latest software release WBS26, due for roll-out in August 07!  You will need Firefox 2.0+ or Mozilla 1.7.13+ with the JVM 1.5 or later.  

Cold Gin, I think your specific problem is unrelated to the fact you're on Ubuntu - I am getting the same error from your URL with a Windows machine.  The URL is probably invalid, kindly request that you source the correct URL from the author.

---

### Post by csi-torchwood on 2007-08-15
BoxDog wrote

>
> WebEx will be supporting Ubuntu Linux 6.10 and 7.04 as of our latest software
> release WBS26, due for roll-out in August 07!
>

I, too, have been struggling with this issue under Ubuntu 7.04 (default Dell laptop installation).  The login screen looks and behaves correctly, and the meeting manager screen looks and behaves normally.  The shared-application screen, however, does not.  The shared-application screen is laid out, apparently correctly, but the actual presentation material from the host shows up as a solid black frame.

This is a big deal for us, a real deal-breaker, and I'd be deeply grateful for any assistance or even hope that you can offer.  Do you have a date for WBS26?  Are there any Ubuntu-specific workarounds in the meantime?

Many thanks,

Frank

---

### Post by precek on 2007-08-16
I have the same behaviour, except of the shared application box appears as white, not black.
Zdenek

---

### Post by irish_flu on 2007-08-16
> **BoxDog said:**
> Hi everybody

I am a WebEx employee and was actually referred to this page by a customer who uses Debian.  I just wanted to let you all know that WebEx will be supporting Ubuntu Linux 6.10 and 7.04 as of our latest software release WBS26, due for roll-out in August 07!  You will need Firefox 2.0+ or Mozilla 1.7.13+ with the JVM 1.5 or later.  

Cold Gin, I think your specific problem is unrelated to the fact you're on Ubuntu - I am getting the same error from your URL with a Windows machine.  The URL is probably invalid, kindly request that you source the correct URL from the author.

Hey thanks Boxdog, that's good info there!

---

### Post by BoxDog on 2007-08-22
csi-torchwood and precek, I've tried to recreate what you're experiencing using Feisty Fawn 7.04 on the new WebEx software (Meeting Center client software version 8.0).  I was able to share Powerpoint presentations, desktops and applications both ways to and from a Windows machine so I think this new version will remedy your issues.

I recommend you touch base with your Customer Services Manager, they'll be able to advise when your site is scheduled for update to WBS26 and if possible/necessary bump it up the queue for you. Hope that helps!

---

### Post by csi-torchwood on 2007-08-24
BoxDog writes that WebEx's latest software, Meeting Center client software version 8.0, appears to work correctly with Ubuntu 7.04 talking to a Windows machine.  This is obviously encouraging.

If I might scrounge one more insight from you, BoxDog, I'd like to make sure I understand which pieces I'm dealing with: What is the relationship between Meeting Center v8.0 and WBS26?

Many thanks.

---

### Post by xyster on 2007-09-06
Can someone please list the steps they performed to install and run Meeting Manager 8 (WBS26) under Ubuntu 7.04 with Firefox 2 and JVM 1.5?

When trying to join a meeting I still receive the message:

"Meeting Center is not available for your computer's operating system. For information about system requirements, please refer to the  FAQ  support. "

Thanks in advance.

---

### Post by str8line on 2007-09-06
Partially related, anyone finding problems with webinars and  online access may want to try accessing the same sites in Opera instead of Firefox/Swiftfox.  While Opera is not an Internet Explorer clone it will display pages as Internet Explorer for those site designers who only code for M$ browser.  I had a problem accessing some course work for work in Firefox and was able to access it no problem from Opera.

Hope that helps some until WebEx (who by the way still requires the use of Microsoft JVM).

---

### Post by VoiceOvGod on 2007-09-06
> **xyster said:**
> Can someone please list the steps they performed to install and run Meeting Manager 8 (WBS26) under Ubuntu 7.04 with Firefox 2 and JVM 1.5?

When trying to join a meeting I still receive the message:

"Meeting Center is not available for your computer's operating system. For information about system requirements, please refer to the  FAQ  support. "

Thanks in advance.

Which URL are you at? (i.e. companyname.webex.com)

Part of this depends on who provides service for your company. I know of some resellers that have not updated their sections to be 7.04 compatible yet. The Meeting Center test is hard-coded, and many companies have not yet updated due to testing proceedures, etc.

---

### Post by xyster on 2007-09-06
> **VoiceOvGod said:**
> Which URL are you at? (i.e. companyname.webex.com)

Part of this depends on who provides service for your company. I know of some resellers that have not updated their sections to be 7.04 compatible yet. The Meeting Center test is hard-coded, and many companies have not yet updated due to testing proceedures, etc.

I am using mpi.webex.com.

How would one go about updating their site to be 7.04 compatible?

---

### Post by VoiceOvGod on 2007-09-06
> **xyster said:**
> I am using mpi.webex.com.

How would one go about updating their site to be 7.04 compatible?


mpi.webex.com is using WBS 25

Currently, your version of WBS does not support it.

From your Meeting Center, click on Support, then Meeting Center FAQs, then What do I need to host or attend meetings?, then click on Cross-platform Features and Known Issues.

Currently, for Linux it only supports RHEL WS 4 and SuSE 10.

To get it updated, you need to contact your Sales rep either at WebEx or the Reseller that you go through.

Sorry :(

---

### Post by precek on 2007-09-11
> **BoxDog said:**
> csi-torchwood and precek, I've tried to recreate what you're experiencing using Feisty Fawn 7.04 on the new WebEx software (Meeting Center client software version 8.0).  I was able to share Powerpoint presentations, desktops and applications both ways to and from a Windows machine so I think this new version will remedy your issues.

I recommend you touch base with your Customer Services Manager, they'll be able to advise when your site is scheduled for update to WBS26 and if possible/necessary bump it up the queue for you. Hope that helps!

To BoxDog: Thanks for your post.  I tested the connection between Ubuntu Feisty Fawn 7.04 (running on HP nc6400 notebook) and Windows/XP today.
Sharing of Linux applications works OK, though in addition to the shared window the remote participants see the whole Ubuntu desktop.
Sharing from Win/XP to Linux still ends up in blank window on the Linux side, though it is possible to control the remote (but invisible) Win/XP application or desktop.

Unfortunately, I don't have any contact info to the CSM.

---

### Post by Vinas on 2007-10-23
> **str8line said:**
> Partially related, anyone finding problems with webinars and  online access may want to try accessing the same sites in Opera instead of Firefox/Swiftfox.  While Opera is not an Internet Explorer clone it will display pages as Internet Explorer for those site designers who only code for M$ browser.  I had a problem accessing some course work for work in Firefox and was able to access it no problem from Opera.

Hope that helps some until WebEx (who by the way still requires the use of Microsoft JVM). That's almost totally incorrect, unfortunately. You do not need Opera to "fool" a website either -- just install the User Agent Switcher plugin for Firefox. :guitar:

---

