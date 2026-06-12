---
title: "wine and lotus smartsuite 9.8"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by alicemoon on 2007-03-31
I have installed wine and it seems to work as I have loaded neomem through it. My main database is on approach, until I figure out glom or base I need to use it so I have tried loading smartsuite millenium 9.8 and intended to do a custom install. However although the setup.exe file opens through wine file and the wizard starts it says it is searching for related applications and then stalls. I have checked the forums and all I can find is some bits about borland database drivers but these are all old posts. Can anyone help me please as I am stuck? -

---

### Post by alicemoon on 2007-04-02
Can anyone help???

---

### Post by alicemoon on 2007-04-03
is amyone there???

---

### Post by bigee1212 on 2007-04-03
wine = very buggy

not every windows program is supported. my advice is to find open source software that fufills your needs, or if you have to, dual boot with windows if you absolutely need that piece of software

---

### Post by Terl on 2007-04-03
Checking over at the Wine site makes this look less promising.  There is no entry for the version cited above but there is an older version with notes that indicate it is not too reliable.  What functionality are you needing?  There are some excellent open source apps that may fill the need as Bigee1212 notes.

---

### Post by alicemoon on 2007-04-03
I have never used microsoft access I started out with lotus and went through a few upgrades with it. I have a database which I use for my business - when I swopped to open office I tried to rebuild it using base but it was just too complicated for me I could not get any joins/relationships to work properly. I am a competant computer user but have no programming or deep knowledge skills. I need a database programme I can set up through a straightforward  interface - I have 6 joined databases in approach which I use to set up jobs, send contracts and invoice. It works very well and if I can get it to work in wine it would be wonderful. The opensource database programmes I have looked at all seem too complicated for me, Glom sounded good but I cannot even open it and looking in forums it seems you have to load a backend database engine first so it's not that simple. If you can offer any suggestions that would be great - thanks for your help.

---

### Post by mikeyphi on 2007-04-03
I guess you really want to use your Lotus!
I run my 'musthave' windows programs in a virtual machine...tried wine but it didn't work for me!
Have a look here  [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Virtual_Machine_Manager_.28VMware_Server.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Virtual_Machine_Manager_.28VMware_Server.29)

---

### Post by Terl on 2007-04-03
I develop M$ Access databases here at work so I am familiar with it.  I am completely self taught.  I am not too familiar with the programs you mention.  Years ago I did play with Lotus 1-2-3 for a while but so many work places use M$ stuff I had to switch.  

If you are familiar with the concepts of a relational database, the Open Office Base should not be too difficult.  You can most likely import existing data and have it create the tables at the same time.  I would experiment with open office.  If you build the new one while keeping the old one it will be easy to validate data as you develop your queries and such.

I even checked the Crossover Linux site [http://http://www.codeweavers.com/compatibility/browse/?app_id=2297]("http://http://www.codeweavers.com/compatibility/browse/?app_id=2297") which is basically an enhanced Wine and even they mention SmartSuite is not supported right now.  It stinks, I know, but all you can do is change or keep a windows install to run your app.

---

### Post by Joneerickson on 2007-04-03
I would suggest trying Win4Lin, It allowed me to run some windows programs that WINE and Crossover both refused to touch.

---

### Post by jvc26 on 2007-04-03
You could try using mysql and the query browser as the front end - also I think that open office is now able to access mysql databases. I've always used mysql as a database environment.
Il

---

### Post by alicemoon on 2007-04-03
thanks for your answers - I shall look at all the suggestions - I do want to use my lotus approach until I find an open source replacement and it looks as if I may need to go and have another try at Base.
Mysql is I think beyond me but you never know!
For the moment I will keep XP for work and try to shift everything over as and when I find a suitable database program that I can work with. I like Ubuntu and will continue to use it on my non-work pc and learn more.

---

### Post by bubbaextra on 2007-08-21
Alicemoon, you seem like you have a handle on things in general.
You are computer literate for real.
You also have and or run a business.

This is my recommendation, continue to run your business as is. You are good at it.

Next, hire a mysql developer to build you a database template to import your data on to.
Then build a web interface for the same.

This would allow you to distribute you application via a web server, easily.
You could update the interface anytime yourself.
It would require little training for new employees, if they can open a web browser.
And best of all, M$ would not make anymore money of your hard work.

Good Luck Alice

Bubba

---

### Post by Tobster on 2007-08-21
I believe that the Close Source version will likely meet your needs.  I would visit:

[http://www.codeweavers.com/products/](http://www.codeweavers.com/products/)

You can e-mail Codeweaver and they will e-mail back telling you if CrossOver will support the software that you need.  I believe it will but please check with them first.  CrossOver is really cheap I think it cost around $20 USA  so that £12 UK.

I found the customer service to be second to none.

Thanks

Toby

---

