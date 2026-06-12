---
title: "This may be a silly question but...."
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by phety001 on 2007-05-06
I am completely new at all this and want to know will microsoft software run in I install Ubuntu on a laptop?
Eg Office 2003?

Will PC games etc run too?

Thanks

---

### Post by bukwirm on 2007-05-06
If you want to run Windows programs on Ubuntu, check out [WIne]("http://www.winehq.org/"). Not all Windows programs work, though.

---

### Post by starcraft.man on 2007-05-06
Office 2003 really isn't needed, OpenOffice is in all respects a fully functional replacement (except maybe for publisher but meh...). There really isn't a need to support microsoft on a linux distro.

In addition to wine, you may also want to check out Cedega (google it), its a GUI front for wine with its own set of extra supported games, it is paid for though... at least, if you want to pay for it I mean.

Try open office though, for word excel and presentations it works well :)

PS: Bukwirm, I'm liking your pic :D

---

### Post by Tundro Walker on 2007-05-06
No, Windows software won't directly run on Linux.  This is due to how they handle the compiled code.  It's kind of like how 2 cars, EG: Honda and Volvo, can't use the same parts (for the most part...EG: a nut and bolt may be interchangeable, but you can't just slap a Volvo radiator into a Honda...it's not designed to fit).  It's the fundamental structure of the OS and how it works.

In Linux / Ubuntu, WINE can be used as a "bridge" or emulator (even though it's very name, WINE = Wine Is Not an Emulator).  Basically, you run WINE to get it to run a program.  Getting it to run or install some Windows software on your Linux machines can be tricky, but if you google the software name and include the words "linux wine", you should come across some web sites explaining how to do it.  EG: "quake linux wine"

However, Linux is not without its own applications.  There are Linux alternates to a lot of Windows software, in essence letting you ditch your old Windows software.  

For instance...

Web browser
* Win = Internet Explorer (or FireFox)
* Lin = Firefox, Epiphany, Dillo, Konqueror (for KDE desktop)

Office Applications
* Win = MS Office (pick your poison...97, 2000, XP, 2003, 2007)
* Lin = Open Office

Multimedia
* Win = Windows Media Player
* Lin = Totem Media Player, Amarok (music), XMMS (like Winamp), etc (there's tons of these things)

Email
* Win = Outlook, Outlook Express, (Thunderbird)
* Lin = Thunderbird, Evolution (like Outlook, since it does email and calendar scheduling)

The limitations on Linux which you will hear a lot about (if you llama the forums, that is), is that Linux...

1) has limited game support (IE: hard to get the latest Windows games to run on it)

2) can't run Photoshop (latest versions don't work with WINE, and there's no Linux Photoshop.  Some folks are happy using GIMP as an alternative, but others are not.  IE: individual mileage will vary.)

3) in Ubuntu, there is limited proprietary format support "out of the box".  IE: it doesn't come with necessary stuff installed to view flash movies, listen to mp3's, etc.  This was a concious decision by Ubuntu developers and Canonical, because in some countries, it is illegal to use proprietary formats without licensing or some such.  (There's legal issues...nuff said).  In United States, there are no such issues, and starting with Feisty Fawn (go Fawn!), they made it easier to install the necessary stuff to get this running.  When I say "install", it's not like a 2 hour click-through on an annoying GUI obstacle course, or hunting down lib's and crap in the repositories.  Fawn is now smart enough to recognize that you're trying to run a proprietary format, and will ask if you'd like to install the necessary lib's, etc to run it, popping up a legal message explaining that it may not be legal to do so where you live (EG: China).  You accept the responsibility of installing the stuff by clicking "Yes", it does the rest, and you're good to go.

Another concern with "switchers" (coming from Win to Lin) is if all their old work from Win will come over.  For the most part, it should.  You can use mp3's, you can open MS Word .doc files in Linux.  But, in some cases, some of your work may get scrapped.  EG: I had quite a few music projects I did in Sony Acid Pro.  I had to scrap them because they were in a proprietary format that only Acid Pro (and some other Windows-based music creation programs) use.

These are the main reasons why some folks choose to dual-boot...they keep their old Windows work, and the ability to play latest games or use Photoshop on it (or whatever Windows only software they're hooked on), but also have Ubuntu installed in their hard-drive, letting them do other things with relative safety...like surf the net...without catching a virus (LOL!)

However, in my opinion, I switching sooner rather then later to be better.  Companies, like Microsoft, are trying to tighten their grip on their proprietary formats.  So, for instance, .doc files made using MS Office Word 2000 can open in Open Office on Linux, but the 2007 .doc format can't...Microsoft changed it, because they don't want users switching over to some other Application.  They want folks locked in to their application, which they charge way too much money for, and eventually want to push folks into some kind of subscription-based monthly charge, since they've pretty much peaked at what it should do.  

(Not what it CAN do...it can probably still get changed to do quite a lot, but, honestly, the learning curve on MS Office is getting so huge, most users don't use more than 25% of the features.  I personally have MS Office Master Certification, and I code in VBA and such...MS Office is practically it's own Operating System these days, and the more crap they add to it makes it harder and harder for the average use to want to use it, since it's more junk getting in the way of the simple task the user wants to do.)

Anyways, I feel folks should switch over sooner, rather than stay with Windows longer and get locked in more and more.  While Microsoft focuses on standardization using THEIR OWN format (IE: everyone uses MS Word, thus .doc has become the standard...so all the other word processor applications are basically shut out of the word processing business since they can't use .doc format), Linux and Ubuntu focus both on standardization AND open formats that anyone can developer software to use.

In the long run, Linux, Ubuntu and Open Source Software (OSS) in general,  are focusing on making quality software without budget or profit getting in the way of decisions.  So, developers can focus on making the best "product" they choose to, without having to think about hobbling it in various ways to produce the "economy" version and the "enterprise" version so they can charge more.  Instead, they just make one really good version...elegant software that gets the job done.

The sooner a person switches, the less painful it will be in the long run.

I hope this helps.

---

### Post by starcraft.man on 2007-05-06
> **Tundro Walker said:**
> 

However, in my opinion, I switching sooner rather then later to be better.  Companies, like Microsoft, are trying to tighten their grip on their proprietary formats.  So, for instance, .doc files made using MS Office Word 2000 can open in Open Office on Linux, but the 2007 .doc format can't...Microsoft changed it, because they don't want users switching over to some other Application.  They want folks locked in to their application, which they charge way too much money for, and eventually want to push folks into some kind of subscription-based monthly charge, since they've pretty much peaked at what it should do.  


Ya, that stupid new format, no worry though. The crack guys at open office will have it implemented before Bill Gates even gets the time to blink :p

BTW: Boy thats a lot of text to type, fingers must be tired after that :p

Oh and one more note, if you don't like gimp's layout, try the gimpshop facelift, you might find it much more natural (Ubuntu people please don't hurt me for suggestion it, I don't use it >.> *hides under a rock*)

---

### Post by CalvinChile on 2007-05-06
If you have software that is not available in Linux, then I recommend to install [VirtualBox]("http://www.virtualbox.org/"), it runs really nice in my  
Inspiron 6400 (1 G RAM, Dual Core).

---

### Post by teddybairs1 on 2007-05-06
Browse through the Add/Remove programs list and see if there's any suitable substitutes for your MS programs. Office in general is handled very capably by OpenOffice.org, which in my opinion puts MS Office to shame for the sheer quantity of file types it can handle.

Where games are concerned, there are a number of good games written for Linux, and there are more added all the time. they don't always have the polish of stuff written for MS, but it's getting better, and they are by and large more challenging in the AI department.

Where desktop publishing is concerned, you can always use Scribus.

And when you absolutely have to have an MS program, try WINE or one of its proprietary siblings Cedega or Crossover Office. But I think you'll find you can do without MS more than you think.

---

