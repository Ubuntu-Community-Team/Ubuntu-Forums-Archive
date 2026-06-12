---
title: "Are there REAL Ubuntu couterparts to MS Access &amp; Street &amp; Trips?"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by WIVO_Riley on 2007-02-01
Hi- sorry if this gets wordy.
Love Ubuntu- dual boot on 1 computer, main OS on 2 others.  Want to convert laptop to it as well, but there are a few programs that I'm having trouble finding counterparts for.  I have a database in Access that I put a TON of work into (access 2003), and rely on Street & Trips with the GPS (Street & Trips can import excel sheets with listed customers dumped from the Access database- which basically automates where I'm going, when, and what route I'm taking.

I can work around and redo the excel sheet as needed (it's REAL big), but the database was a TON of work to get set up and running. 

No Street & Trips counterpart- no converting over to Ubuntu 100%
No Access counterpart- no converting over to Ubuntu 100.

The words "street", "trips","access", etc. get lost in the bazillion returns while I've been searching for this- I find some glimpses of hope, but nothing real.

Any help at all would be appreciated.  

BTW--I've looked at CX Office- which may help the Access situation, but I think I have some backward compatable issues with my 2003 version (they only support 2000 (although still "buggy" according to them- not acceptable to me)

......sitting here crossing fingers and prayin'.....

Riley

---

### Post by psyne on 2007-02-01
If it is really mission critical then you could use crossover office or wine to set it up. 

However you should be able to import the information into open office using Open Office Database and Spreadsheet unfortunately I don't know of any alternatives to streets and trips for you to try. Best bet I would reccomend trying the Crossover office it is very easy to use and well supported though it does cost. But if you are dependant on it then it is a small price to pay, if you can't afford it then you should be able to get wine working though not with the built in features of crossover. I personally use crossover and I have not had any problems with backwards compatibility. Though I have ultimately ended moving completely over to Open Office.

Another possibility is using a Virtual Server and running a minimum install of windows just for that purpose.

---

### Post by meng on 2007-02-01
Welcome to vendor lock - you put a lot of work into a document (in your case a database) only to find it can't be ported elsewhere. Unfortunately, like almost every other (former or current) Windows user, the realization doesn't come until it's "too late". I'm not trying to say "I could have told you so", or that you ought to have used mysql or something similar before you put all that work in, but I am lamenting that you're "stuck" with Microsoft as far as those functions are concerned.

---

### Post by WIVO_Riley on 2007-02-01
> **psyne said:**
> If it is really mission critical then you could use crossover office or wine to set it up. 

However you should be able to import the information into open office using Open Office Database and Spreadsheet unfortunately I don't know of any alternatives to streets and trips for you to try. Best bet I would reccomend trying the Crossover office it is very easy to use and well supported though it does cost. But if you are dependant on it then it is a small price to pay, if you can't afford it then you should be able to get wine working though not with the built in features of crossover. I personally use crossover and I have not had any problems with backwards compatibility. Though I have ultimately ended moving completely over to Open Office.

Another possibility is using a Virtual Server and running a minimum install of windows just for that purpose.

Mission Critical?  Well, my slow season is about at an end, so it would have to wait till late fall.  Sounds like I may be disappointed with the "Silver" rating CXo gives their Access version.  I would LOVE to move completely out of MS's reach into my wallet.  

Do you have personal experience with both Access and Oo Database?  The amount of data I have in the database is small compared to the things I can do with it- I drove myself half-nuts writing countless expressions and queries.  Am I going to end up driving myself completely nuts rewriting?

A separate dedicated GPS wouldn't be the worst if I could upload the exact locations for use by the crews somehow.

Thanks again.

---

### Post by szf on 2007-02-01
For an Access 2003 equivalent, perhaps [Glom]("http://www.glom.org/wiki/index.php?title=Main_Page") would fulfill the need. I dunno about FOSS GPS streets and addresses, though.

---

### Post by WIVO_Riley on 2007-02-01
> **meng said:**
> Welcome to vendor lock - you put a lot of work into a document (in your case a database) only to find it can't be ported elsewhere. Unfortunately, like almost every other (former or current) Windows user, the realization doesn't come until it's "too late". I'm not trying to say "I could have told you so", or that you ought to have used mysql or something similar before you put all that work in, but I am lamenting that you're "stuck" with Microsoft as far as those functions are concerned.

"Vendor lock" lol.  Yup- I guess I never looked at it like that before.  I self-taught how to use access, and ended up stuck with it... great.

I use the GUI in Access for all of my stuff- I'm self taught, and learning code wasn't going to pay the mortgage.

SO.... now that I'm here.... where do I go from here?

I'm very impressed with Ubuntu (got Beryl crankin too- it rocks)  Kid plugs in the Ipod- no problem.  Evolution kicks the CR@P out of outlook imho, syncs with my palm, etc etc.  
If I could just clear these hurdles- which now look to be about forehead tall- I'd be another 100% convert.  2 of my kids already are and really never noticed! lol

Thanks in advance

---

### Post by WIVO_Riley on 2007-02-01
> **szf said:**
> For an Access 2003 equivalent, perhaps [Glom]("http://www.glom.org/wiki/index.php?title=Main_Page") would fulfill the need. I dunno about FOSS GPS streets and addresses, though.

Glom looks like an interesting candidate- MUST be able to interact with Oo spreadsheet though.  I'll have to spend some time researching it some to see if it will work.  
Thanks

---

### Post by meng on 2007-02-01
Well for a start, don't feel down about continuing to require some Windows for the present time. It's not uncommon for new Ubuntu users to dual-boot. Indeed, I was 100% Windows-free for months, only to reinstall Windows for a couple of games and game-related applications (constituting less than 5% of my use). You seem to have a positive attitude, which is a very handy attribute, and if you're interested, there are plenty of books or web tutorials on using mysql, postgresql, etc. and although you'd likely begin with learning how to use a basic text interface, there are GUIs available (or else you could learn to program your own GUIs!!)

I'm not a database guru, although I dabble. It's good to go back to basics to refresh concepts like sensible database structure (perhaps you're already quite well-versed with normalization, for example). I haven't heard great things about Openoffice Base.

---

### Post by WIVO_Riley on 2007-02-01
> **meng said:**
> Well for a start, don't feel down about continuing to require some Windows for the present time. It's not uncommon for new Ubuntu users to dual-boot. Indeed, I was 100% Windows-free for months, only to reinstall Windows for a couple of games and game-related applications (constituting less than 5% of my use). You seem to have a positive attitude, which is a very handy attribute, and if you're interested, there are plenty of books or web tutorials on using mysql, postgresql, etc. and although you'd likely begin with learning how to use a basic text interface, there are GUIs available (or else you could learn to program your own GUIs!!)

I'm not a database guru, although I dabble. It's good to go back to basics to refresh concepts like sensible database structure (perhaps you're already quite well-versed with normalization, for example). I haven't heard great things about Openoffice Base.

WHOA there! lol  I'd have to stick with GUIs for the foreseeable future.  No time for extended self-training- unless it's easy to pick up (doubtful).  

I estimate and manage concrete and asphalt paving projects for a living- I'm on the road in the car 10hrs a day.  The computer I use 99% of the time is the laptop that rides next to me on a platform in the car.  I dual boot my nice new desktop at home, but the laptop is getting elderly and I have no extra room for a dual-boot- I'm running an 80 gig Ext HD 100% of the time on it now.  I read ubuntu unleashed twice and ubuntu for non-geeks, and have come a long way on my own in the last 10 years or so.

Normalization?  Ah, no... lol  I think if someone who was formally trained in constructing Access databases got under the hood and poked around in mine to look at the way I got the results I wanted, they'd have a lethal gripper on the spot. 

I prefer to sit and think how I could get the program to do what I wanted, and then proceed to do do exactly that.  If it were a car, it may look like a bowl of spaghetti under the hood.

You haven't heard great things about the Oo database?- meaning you have heard bad things or haven't heard anything about it?

What about "glom" mentioned above- any thoughts?

Thanks for your  time all of you- the help is much appreciated

---

### Post by meng on 2007-02-01
What I mean about OO Base is that I have heard some bad reviews and no good ones. I'm ignorant about glom.

---

### Post by WIVO_Riley on 2007-02-01
> **meng said:**
> What I mean about OO Base is that I have heard some bad reviews and no good ones. I'm ignorant about glom.

Thanks Meng... a bunch.

I installed glom and will play a bit and see if it's something possible.

Still remains to be seen if it will play nice with spreadsheets.

---

### Post by GWoitena on 2007-03-15
Google Earth will plot a trip.  GE works well if you're traveling down main roads and in metro/suburban areas. But it gets questionable if you're trying to route to out of the way rural areas.  To use GE efficiently, you need your graphics card configured for 3D acceleration or else it will drag.

---

### Post by hyper_ch on 2007-03-15
Hmmm, depending on your computer you could consider running windows in a virtual machine... I assume you have a rather new M$ Office version? Or do you maybe have older ones? I was thinking if it's just those two appz that you need to run then you could install Win98SE in VmWare or VirtualBox or Xen and run it inside ubuntu... then you can use Ubuntu and still have the database working as long as you find no way to make it also work in Ubuntu the way you want to... if it's a newer Office version then you may need to use Win2000 WinXP which will, of course, require more system ressources than Win98SE does...

Btw, can M$ Access data be exported as SQL or CSV?

---

### Post by mediax on 2007-03-15
> **WIVO_Riley said:**
> WHOA there! lol  I'd have to stick with GUIs for the foreseeable future.  No time for extended self-training- unless it's easy to pick up (doubtful).

Access will convert its query designs to SQL for you - open the query and use the same button as you use to enter design view (the set square button), but click the dropdown arrow and select SQL.  This will display the SQL equivalent of that Access query, which you can then copy and paste.

It's not particularly elegant code (FAR too many brackets :lolflag: ), and certain advanced features (such as UNION queries) can cause problems, but it's how I generate much of my SQL code at work - oh dear, my secret's out! :oops:  - and it's particularly useful when you're beginning SQL.

---

