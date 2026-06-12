---
title: "Bunch of Small Issues...comment freely"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by salaberrios on 2007-07-23
I post this in the beginner section because it should be self explanatory.

Apache- I have installed Apache2, MySQL, PHP5. Here is the list of my issues (that I'm having ;-)
How do I run Php Admin?

How do I set up websites in Apache2? I spent all day reading the tutorials and even some of the current issues. I have copied the default and changed the name to my site name. I editted the file to point  to the directory conatining the site content. I can open a browser, type [http://localhost](http://localhost) and get a welcome message for nanoweb, but I can't do anything else. I can't pull up the index, nothing. I keep getting errors.

I have a Dell Power Edge 1600, and I currently use teh generic video drivers at 1240. Which is cool, but all the text looks fuzzy sort of. I would like a better resolution if possible. I tried loading ATI drivers, but I could not recover afterwards, ended up reloading Ubuntu after spending 4 hours reading for a fix. I tried all the fixes and the issue got worse, Any thoughts? 

I seem to have every upgrade and update installed. Just need to set a web site and access it successfully. I can figure out the other stuff. AND I tried changing permissions on every file imaginable, so that can't be the issue....can it? LMAO!

---

### Post by DBStevens on 2007-07-23
What index are you trying to pull up?

Could you post the contents of the modified 000-default file?

---

### Post by DBStevens on 2007-07-23
For the myphpadmin try this link in a browser:

file:///usr/share/doc/phpmyadmin/Documentation.html

---

### Post by salaberrios on 2007-07-24
Thanks for you rreplies. 

Ok, I made some head way. I am trying to test 3 different sites just so I can get the gist of this.

One site, I input the local IP to the server in URL and it comes up. 192.168.1.7 (mapped to a static IP on the WAN side)

Second site comes up when I type [http://localhost/](http://localhost/)

Third site does not come up at all.

The first site is the only one I configed with the IP as a NameVirualHost AND Virtual Host in the enabled-site file. The other two along with the first have /var/ww/ site content folder filled in to map the location of the site files.

Before I assign DNS I would like to make sure these sites work locally and can be accessed from the browser so I limit the remainder of my troubleshooting to DNS issues.

Thoughts? BTW- I am a beginner with Linux based systems. Tons of WIndows experience but I just started messing with Web servers. This inffo is to gauge and excuse my choppy explanation of this issue.  Thanks for your help in advance.

---

### Post by DBStevens on 2007-07-24
Without the configuration information I have zero to go on.  You at least have a working server.

Good luck.

---

