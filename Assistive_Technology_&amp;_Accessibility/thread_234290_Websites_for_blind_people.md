---
title: "Websites for blind people"
date: 2006-08-11
forum: Assistive Technology &amp; Accessibility
---

### Post by covenant on 2006-08-11
Greetings to all.
I am using Ubuntu 5.10 to develop webpages. MY current task, is to design a website for people with low vision and blind people. 
I am starting to do research on the subject, and I'm learning and starting to see things in a new way.
Could please someone point me in the good direction, regarding screen readers? I've installed Festival, and I want to be able to use Lynx or ELinks with it, but I can't make interaction between those two applications.
All help on this accessibility topic is very wellcome.
Thank you

---

### Post by Henrik on 2006-08-11
Festival is just a speech sythesiser that converts text to speech. You will also need a screen reader that captures text from your environment and feeds it to the synthesiser.

If you are on the pure command line then you need something like the Speakup kernel module. If you are in Gnome you can use Orca or Gnopernicus. See: 

[https://wiki.ubuntu.com/Accessibility/doc/Speakup](https://wiki.ubuntu.com/Accessibility/doc/Speakup)
[http://live.gnome.org/Orca](http://live.gnome.org/Orca)

---

### Post by Senak^2 on 2006-09-11
I find it easiest to test webpages for blind people with a program called JAWS which is claimed to be the world's most popular screen reader. Unfortunately it is only available for Windows and is most compatible with Internet Explorer. I recommend that if you do choose to use JAWS that you read the documentation about using the keyboard shortcuts (which are essential). You can download a free demo* of JAWS from their website.

[http://www.freedomscientific.com/fs_products/software_jaws.asp](http://www.freedomscientific.com/fs_products/software_jaws.asp)

Sorry I don't have much experience with Linux screen readers so I don't have much more to say. Good luck with your research and I hope you'll make things more accessable and less annoying!

*The program doesn't expire after 30 days or anything but it will only run for 45 minutes at a time. If you want to use the program after your 45 minutes have expired you'll have to restart your computer.

---

### Post by NiceGuy on 2006-09-11
I'd recommend jaws as well and I have it on good authority that it is, as claimed, the most popular screen reader. But as previously mentioned, its only for windows. IMHO this is one area which linux is really lacking in.

Anyway, what I'd suggest is that you make heavy use of css for both layout and formatting. What your aiming for is a site which will produce clear, easy to read plain text when the style sheets are removed. Also make sure you use the heading tags appropriately (ie H1 for main titles, H2 for sub titles etc.) as that helps screen readers identify headings and also helps if the user has a custom style sheet which they use. Where possible avoid tables and defiantly avoid frames! Hurm... what else... oh avoid confused images and fancy graphics and if you do have graphics then make sure the alt text is properly filled in.

That's all I can think of off the top of my head, if you like you could post the url of the site and we (the ubuntu community) could have a look at it, or if not then feel free to PM me and I could have a look as I have more than a bit of experience in making accessible websites.

---

### Post by wylfing on 2006-09-11
I concur that proper CSS usage is key. My site is 100% divs with CSS, renders fine in IE and Firefox and Opera and Konq, etc.

I usually take a look via Lynx, and that is what usually shows the quality. If it renders fine in Lynx, it'll render fine in any screen reader.

---

### Post by andrew_stephenson on 2006-09-19
Hi there,

There are a few things to bear in mind when creating websites for those for are blind or partially sighted (in no particular order...!):

-> Always use relative font sizes so those who are partially sighted can increase the text use the browser.  
-> Additionally, you may wish to include some links in the top right-hand corner that increase and decrease the text size using javascript (some people don't know you can change text size through the browser)
-> For your navigation, use the <ul> and <li> tags to create a list as this helps those using screen readers (it tells them how many items in the list and which item they are at)
-> Try not to include images that could easily be replicated using CSS (text in these images cannot be increased through the browser)
-> Make good use of page headings and in a logical order
-> Have a heading before every section of the web page (navigation, main content, newsletter sign-up) as this helps screen readers identifier to their user where they are.
-> For decorative images DO NOT include alternative text!
-> For other images, put EXACTLY what is written in the image in the alternative text (if your logo says 'pink link' then put 'pink link' in the alternative text, NOT 'pink link logo'!)

Hope this hasn't bored you! For more accessibility & usability tips, check out my website - [http://www.pinklink.biz]("http://www.pinklink.biz")

---

### Post by stewski on 2006-09-25
Some good tips on this thread.
I am also working on accessibility in my website designs and (in addition to other suggestions) would point you at

[http://sourceforge.net/projects/fangs/](http://sourceforge.net/projects/fangs/)

a screen reader emulation/helper extension for firefox that can be useful during the design process.

I'm hoping to use some back end processing/template switching to offer a fully optimised version of the site content for improved accessibility.
I'm looking to use

[http://www.modxcms.com](http://www.modxcms.com)

which is a open source content management project which seems to have a good focus on both accessibility and other w3c recommendations.

great thread so far and keep the tips comming.

One neat addition Ive seen on some sites is a skip to main content (or skip nav) link before the navigation so that once a correct page is selected screen readers would not have to talk through the navigation should the user wish to jump to the content. This can be very useful dependant on your source order, site content and structure...

Good luck and perhaps link your sites as they develop so we can see/share tips...

---

### Post by Colonel Kilkenny on 2006-09-27
Not sure if this will help anything but Opera in Windows has a built-in voice-feature. It will read pages after you have enabled it and downloaded the voice package (both done through options).

This has already been said but the most important key is to use correct and standard code and tags like <emph> etc.

---

### Post by SyCo123 on 2007-11-09
Just tried out Opera voice and it's a very cool feature however it doesn't have container identifiers while reading. You can select all right click and speak the page but there nothing to say this is a heading or tabular data etc.

Don't get me wrong like i say I think it's cool, just for a screen reading web dev tool it lack a few features.

---

### Post by Turtlecatpurrz on 2007-11-16
I am a blind person, and although I agree with most of what has been said thus far, I disagree concerning the necessity of putting in alt information for  pictures. Even if pictures are just decorative, I like to know that they are  there, and what they are. I know that the National Federation of the Blind has information on web standards to make pages easily accessible, sadly I don't know where those standards are found on their site. If you want to browse though, the site is [www.nfb.org](www.nfb.org) 

Also, I don't know if this would interest you, I can give you the names and web addresses of the other major screen readers  that are emerging for windows, or that are being regularly used, at least in North America.  These are in no particular order, and I am mostly just using JAWS myself, but I know a little about each programs strengths and weaknesses.  

Sadly, I can't help with Linux.  I don't have a system that I can use with it any longer.

Hal/Supernova (Dolphin) [http://www.yourdolphin.com/productdetail.asp?id=5](http://www.yourdolphin.com/productdetail.asp?id=5)

Not always the best on the web, but very interesting because of the nearly fully portable option. (You have to install special intercept software, before the pen drive will work.)  Dolphin is mostly sold in Europe, though it has recently garnered some attention in North America.

Jaws (Freedom Scientific)
[www.freedomscientiific.com](www.freedomscientiific.com))

 Suffice to say it is very well known, and the majority of American users will be using this package.   It is lagging behind several other companies in Vista development. Despite this and because of its long history, it  is the most widely used in business, and school environments.  It is good to test with JAWS for this reason.

System Access (Serotek)

[www.serotek.com](www.serotek.com)

Has many of the same keystrokes as Jaws, so developers using this program to test will find it more comfortable to learn than some of the others.  Very new, and very exciting because it allows for true access anywhere, you have... Windows and IE.  It looks very hopeful though, and you can try the beta version of their screen reader by typing in [www.satogo.com](www.satogo.com) on a windows machine.  (Only works on IE at this time.)

Window Eyes (GW Micro)

[www.gwmicro.com/](www.gwmicro.com/)

Second in popularity only to Jaws,  this program tries to work more with the MSAA standards than Jaws does.   Can read some pages that Jaws can't so it could be a good tool for determining why a page is difficult to use.  

I don't know if this is actually helpful, especially on the Ubuntu list, but I wanted to try and help anyone who is working to make their  websites easily accessible for everyone.  

Oh, one other thing.  If you have a forum that will be installed, or another process that you wish to protect from bots, please, please, please, avoid picture-only captia systems at all costs.  Inaccessible captia  is the quickest way to shut me and every other blind person I know of,  out of participation with your website.

---

### Post by h24k on 2009-03-24
Hi there im new to the site i have jaws professional screen reading software for sale which is brand new and costs around £3000 its on ebay at the moment item number 250392769340 its the enterprise edition which means multiple user can use it, didnt really know where to advertise it so i thought maybe it would be of help to someone on here? Thanks

---

### Post by h24k on 2009-03-24
On ebay item number 250392769340

---

