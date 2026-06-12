---
title: "Internet explorer"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by RDUBBALO on 2007-03-15
I installed Internet explorer to use for my school homework. its a site called coursecompass.com and i have ie6 working fine just when i go to do the homeowrk the page wont display. It is made for windows and ie only, but i guess i need quicktime and adobe to run it and I have installed the adobe but it doesnt display the page. Any ideas on this. I have to do the homework and I dont have windows at all anymore.

---

### Post by lahook on 2007-03-15
firefox won't work at all ? 
here's  their system requirements

problems i see are shockwave, test gen, and my mathlab

what about trying Opera or Konqueror identified as IE6?


 	Operating Systems  	Browsers*
PC 	Windows® 2000 	

Internet Explorer®, Version 6.0
Netscape® Navigator®, Version 7.0
Windows XP 	

Internet Explorer, Version 6.0

Netscape Navigator, Version 7.0

Firefox 1.0.7
Mac 	Macintosh® OS 9.2 	

Netscape Navigator, Version 7.0
Macintosh OS 10.1 	Netscape Navigator, Version 7.0
Macintosh OS 10.2.x 	Netscape Navigator, Version 7.0
  	Macintosh OS 10.3.x 	

Netscape Navigator, Version 7.0

Firefox 1.0.7

Safari 1.2

* If you have earlier versions of these browsers, you can download a newer version from the appropriate manufacturer's website:

    * For Internet Explorer, go to [http://www.microsoft.com](http://www.microsoft.com)
    * For Communicator or Navigator, go to [http://www.netscape.com](http://www.netscape.com)
    * For Firefox, go to [http://www.getfirefox.com](http://www.getfirefox.com)
    * For Safari, go to [http://www.apple.com](http://www.apple.com)

AOL and AT&T Yahoo users:You cannot view CourseCompass using the AOL or AT&T Yahoo browsers. You can, however, use AOL or AT&T Yahoo as your Internet Service Provider to access the Internet, then open either the Internet Explorer or Netscape Navigator browser within AOL or AT&T Yahoo to access CourseCompass. 


Additional software
To use multimedia material provided with some courses, you may also need to download and install additional software. If you're uncertain whether you'll need these resources, you can open your course and see what it requires. Note that some plug-ins are not supported by Internet Explorer V5.5 SP2 or higher.

    * MyMathLab Installation Wizard - Needed to install plug-ins (such as MathXL® Player, InterAct Math plug-in, the TestGen plug-in appropriate for your course and more) specific to your MyMathLab course. The MyMathLab Installation Wizard is typically found in a course announcement or as a course menu button.

    * Adobe® Reader® - Needed to view online CourseCompass guides and other PDF documents.

    * Apple® QuickTime® - Needed to view full-screen video and streamed media, or hear audio files in any of 30 audio, video, and image formats, including Flash.

    * Java™ Plug-in - Needed to view the Virtual Classroom and Chat sessions in CourseCompass.

    * Macromedia® Flash™ - Needed to improve viewing of high-fidelity web sites.

    * Macromedia Shockwave® - Needed to run animations in some courses.

    * RealNetworks® RealOne™ Player - Needed to hear music or watch streamed media animations in some courses.

    * TestGen Plug-in - Needed to view and take online TestGen tests in CourseCompass.

---

### Post by dstew on 2007-03-15
Maybe this would help.

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

You need to install wine to make it work.

---

### Post by RDUBBALO on 2007-03-15
No I already have Internet explorer 6 working just find. The problem is with the website. I can get logged in but I cant go to the homework page. i need thos eplugins. and It requires a pc OS and it wont work on Linux I want the site to see my computer as windows thaty why I used wine to get the IE6.

---

### Post by ZeroVerteX on 2007-10-16
Running into the same problem. I fixed up an older laptop for my bro to take to college. Loaded it with Ubuntu 7.04. I've got IE6 loaded via ies4linux, but can't get the MathXL plugin to install at all. Some dude got it going per his blog post [http://matthewpoer.freehostia.com/wordpress/2007/09/21/activex-for-linux/](http://matthewpoer.freehostia.com/wordpress/2007/09/21/activex-for-linux/)

If I find anything, I'll gladly post the results.

---

### Post by matthewpoer on 2007-10-17
I currently use Debian GNU/Linux "Etch" with Internet Explorer 6.0 on the MyMathLab web site.

Here is what I did to achive this:
[LIST=1]
[*]Download the installer scripts for IEs4Linux and run it.
```
wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
tar zxvf ies4linux-latest.tar.gz
cd ies4linux-*
./ies4linux
```
[*]Run 'ie6' from a terminal, or start it via a desktop icon if you created one
[*]In IE6, Click Tools>Internet Options>Security (Tab)>Slide to Low. This allows web pages to install the activeX scripts. It isn't really a security threat, because you'll only be using IE6 for this web site, and nothing else. (unless you just want to use it...eww)
[*]navigate to [http://portal.coursecompass.com/portal/Login](http://portal.coursecompass.com/portal/Login)
[*]Log in
[*]Click for the appropriate class in the class listings
[*]Click Do Homework
[*]Now I am prompted to install various plugins and scripts, because I do not have them
[*]Go ahead and install the ActiveX plugins (clicking 'next' and 'okay' and such a lot)
[*]Okay the MathXL Installation Assistant 1.2  and the MathXL Player version 4.5.0.4 are Installed.
[*]**Ignore the PDF and QuickTime plugins**, you don't need them for homework. If/when you need a PDF or video file, just save it to your desktop and open it with the appropriate application. I also neglected the TestGen plugin, which I do not need. 
[/LIST]

Okay so if you have followed all of those steps, let me know which part went wrong for you. Also note wheather you used the general download/installation method (above) or the specified Ubuntu instructions from the web site.

---

