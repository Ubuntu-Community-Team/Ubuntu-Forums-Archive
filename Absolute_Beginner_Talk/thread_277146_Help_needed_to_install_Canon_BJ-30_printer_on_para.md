---
title: "Help needed to install Canon BJ-30 printer on parallel port - Anybody - Pleez!!!"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by mac_an_ultaigh on 2006-10-14
Well... My first ever install of Ubuntu/Linux on an old Fujitsu-Siemens laptop was truly amazing. So much easier than any version of Windows or Mac I've ever dealt with (and over the past 20 years I've had to deal with most of 'em I'm sorry to say!).

First-time boot came with the full 1024x768 display without having to install any drivers at all! The Gnome interface looks crisper, neater, more elegant and more intuitive than any version of Windows or Mac I've ever encountered. What's all the fuss about Linux being difficult I said to myself. Why isn't everybody doing it?

Then I tried installing a basic Canon Bj-30 printer on the parallel port.

The wizard (System > Administration > Printing > New Printer) said "hp no_device_found."

No problem. The dropdown gave the option of LPT #1, Parallel Port #1 (Canon) and Parallel Port #1 (Epson). Easy-Peezey I said to myself as I chose Parallel #1 (Canon). The Forward button produced a list of printers with the BJ-30 at the top and bj200 as the recommended driver! What a no-brainer I said smugly to myself as I selected it, hit Forward, then Apply, then Properties then Print Test Page.

What a nightmare!

The printer fed one line then beeped. Then another couple of lines and beeped half a dozen times more. Then proceeded to bumb and grind and beep its way printing out a whole page of gobbledygook. Then it loaded another page and did the same. Then another, and another, and another. After more than 10 I pulled the plug on the printer and rebooted the laptop. I switched the printer on and it started grinding its way through another 10 pages!

So I hit the forums and found... well not much really, apart from advice to hit linuxprinting.org

I did that 2 days ago, and I'm still trying to make sense of it.

The Printer Database recommends the gutenprint driver above the bj200. The bj200 was useless, so gutenprint is obviously the way to go.

The gutenprint link takes me to Driver: Gutenprint.

"If you got Gutenprint with your operating system distribution, use the printer setup program coming with your distribution."

Well... Been there, done that, printed out 30 pages of gobbledegook and used up a whole ink cartridge proving it. What else can I try?

"Otherwise it is recommended to use the CUPS driver if you use CUPS as your printing system or the IJS driver if you use another spooler."

OK, so I obviously need to learn about CUPS - whatever that is!

The "CUPS Quick Start" page is - well - extensive to say the least. Packed with all sorts of things I know nothing about but obviously need to spend hours trying to get to grips with - Ghostscript, gimp-print, Foomatic... But is all this really necessary? Why do I need to re-invent the wheel and undergo what looks like a semester-long self-taught programming course before I can print out a letter?

Scroll down half a page to 5) Configure Cups and it says:

"The simplest way is to walk through the Add Printer wizard in the CUPS web interface at http://localhost:631/admin."

OK. That sounds more like it.

I try it. It doesn't work!

Why?

Another half-hour frantic searching (using Windows!!! thank God for broadband) takes me to: CUPS Printing Setup Mini-HOWTO

That sounds just the ticket. Why didn't I find that before.

But hang on a minute. Mini-HOWTO??? It's 22 A4 pages long!!! How long will it take to read all that?

General printer setup with CUPS says that "the easier way is the built-in web interface of the CUPS system. You reach it with any web browser accessing the address:http://localhost:631/"

Then, half a page down, it says: "On Ubuntu Linux the administrative tasks of the CUPS web interface are disabled by default. They say that this is for security reasons. To re-enable them, add the user "cupsys" to the "shadow" group in /etc/group."

Ah-hah. So that explains it. So now I have to add the user "cupsys" to the "shadow" group in /etc/group.

But where do I go to find out how to do that?

You can see I'm struggling a bit here. Thing is, I can't think of anybody I've ever met who wouldn't be. This would be enough to put most people off linux for life.

All I want to do is install one of the oldest and simplest printers on one of the oldest interfaces.

Surely somebody must have written a simple Ubuntu HowTo by now?

If they haven't then if somebody could walk me through how to find what I need to know to print out a letter then I'll gladly write one myself!

---

### Post by petri on 2006-10-14
Sorry to hear that, I have similar problems wiht my Epson Sytlus Color 600 and I did have those problems already in windows. The only thing that stopped the gobbledygook was to rip off all the cables from the printer :rolleyes:  and let it be for a few minutes. I didn't find your BJ30 in [printer wiki]("https://wiki.ubuntu.com/HardwareSupportComponentsPrinters") as I don't find mine either. I don't know what to do so I can't help.

Canon has a site where you can go in and make a request of drivers to your printer, of course there is no garanties that they will write drivers but you can always try. [http://www.canon-europe.com/Support/Software/Linux/registration.asp?ComponentID=312222&SourcePageID=369466#1](http://www.canon-europe.com/Support/Software/Linux/registration.asp?ComponentID=312222&SourcePageID=369466#1)

---

### Post by Sef on 2006-10-14
Did you check out [LinuxPrinting?]("http://linuxprinting.org/show_printer.cgi?recnum=Canon-BJ-30")

---

### Post by mac_an_ultaigh on 2006-10-14
Thanks guys. It's my first post here so your replies are even more appreciated than usual. :D > **petri said:**
> Sorry to hear that, I have similar problems wiht my Epson Sytlus Color 600 and I did have those problems already in windows.Sorry to say that the BJ-30 has always worked beautifully in Windoze. Sorry, because I've been wanting to get away from MS ever since I got my first mug's eyeful of DOS 3.2. I was so hoping that Ubuntu was going to be the end of all that. :-k  > **petri said:**
> The only thing that stopped the gobbledygook was to rip off all the cables from the printer :rolleyes:  and let it be for a few minutes.Yep. Exactly what I did too. But I was amazed at how long it took before everything reset itself.> **petri said:**
> Canon has a site where you can go in and make a request of drivers to your printer, of course there is no garanties that they will write drivers but you can always try. [http://www.canon-europe.com/Support/Software/Linux/registration.asp?ComponentID=312222&SourcePageID=369466#1](http://www.canon-europe.com/Support/Software/Linux/registration.asp?ComponentID=312222&SourcePageID=369466#1)A very long shot methinks. But no harm in giving it a go just for the hell of it :evil:
But to do all that I still have to use Windoze. :cry:
Guess what I'm saying is that if Ubuntu is going to do what it says on the tin and make Linux accessable to a wider user-base then surely providing some relatively trouble-free route to installing bog-standard printers on bog-standard ports has got to be pretty near the top of the list of things to do?> **Sef said:**
> Did you check out [LinuxPrinting?]("http://linuxprinting.org/show_printer.cgi?recnum=Canon-BJ-30")No I didn't. But I will now, and I'll report back here on how it goes.

Thanks again for the feedback. Very much appreciated.

---

### Post by mac_an_ultaigh on 2006-10-15
> **Sef said:**
> Did you check out [LinuxPrinting?]("http://linuxprinting.org/show_printer.cgi?recnum=Canon-BJ-30")OK. I checked this link out and discovered it takes me to the same printer database page at linuxprinting.org referred to in para 9 of my first post:> **mac_an_ultaigh said:**
> So I hit the forums and found... well not much really, apart from advice to hit linuxprinting.org

I did that 2 days ago, and I'm still trying to make sense of it.This is the point where I get stuck in the first place.:(  

The rest of my post describes how difficult it is to find your way through the mass of information from that point on. ](*,) 

I think what I need to do now is to uninstall any drivers already installed by the Gnome Printer wizzard and then install the gutenprint bjc-30 driver.

I'm sure it's easy when you know how. No doubt all the necessary information can be found somewhere on the linuxprinting.org pages. It's just that there's too much of it and too many options for a n00b to get any kind of handle on. All I need is some kind of guidance through the maze from someone who understands such things :)

---

### Post by mac_an_ultaigh on 2006-10-15
OK. Sorted. =D> 

I promised to write a HowTo, so here it is:

**1) ADD USER "cupsys" to the "shadow" group in /etc/group**
IN GNOME MENUS:
- System > Administration > Users and Groups
- Select 'Groups' tab
- Check 'Show all users and groups'
- Scroll down Group list, select 'shadow' then click 'Properties'.
- In 'Settings for Group shadow' dialogue box, scroll down 'All users' list, select 'cpsys' then '+ Add' then 'OK'.

**2) REBOOT CUPS**
IN GNOME MENUS:
- Terminal
sudo /etc/init.d/cupsys restart

**3) ADD PRINTER IN CUPS WEB INTERFACE**
IN FIREFOX:
[http://localhost:631/admin](http://localhost:631/admin)
Enter User & Password
THEN...
As the man said... "The simplest way is to walk through the Add Printer wizard in the CUPS web interface."

And he's absolutely right! If you get that far, it is a WALK-THROUGH. OK, it's a lot slower than it is under Windoze, but the BJ-30 now prints without any bumps or grinds or beeps.

**ADDENDUM**
Thanks to the 'simplicity' of the CUPS web interface I discovered that the gutenprint driver for the BJ-30 was called BJC-30. Guess I should have guessed that! But where does the 'C' come from?

Call me old-fashioned, but I like to know these things. If it had been a G for gutenprint then maybe I just might have guessed.

Whatever... I remembered I'd seen something like that in the Gnome Printers setup.

So I went back to the New Printer wizard in the standard Gnome Printers GUI and, sure enough, there was a BJC-30 driver.

So I selected it. And - yes - it turned out to be exactly the same gutenprint driver that I'd just spent 3 days trying to install. And - yes - it works exactly the same as the one installed through the CUPS web interface. 

Moral of the story is this: Why wasn't that very simple fact made clear at the outset?

On my first ever linux installation, I've discovered that all the programming you need is already there. It's just the support and documentation that isn't!

Before all you old linux hands get on my case, let me say this. There has always been, and there always will be, a vast gulf between the kind of documentation developers need, and the kind of documentation that ordinary users can understand.

Let me explain. My first-ever contact with a computer was in the sixties. Way back then, a 20 MB disk was as big as a washing machine, the CPU was made out of valves and stretched half-a-street long, data input was from punched cards or tape, and output came with a dull machine-gun rattle from striped and sprocketed paper on a teletype terminal. The whole kit-and-caboodle had to be maintained at 5 ppsi above atmosphere to keep out the dust, so talking to the white-coated admin was not possible without entering an airlock! Those of us who were of the opinion that this was not the best-of-all-possible-worlds and  that the most desireable goal was not to reduce the code down to the smallest possible space, but to expand it to produce a more user-friendly environment - like on some kind of television set for instance - were not well received :-# 

Forty years later we are in a world where even the most dyed-in-the-wool linux freak would never dream of suggesting that we could do without a television - VDU - CRT - LED - interface.

Those of you who understand what I'm saying, will. Those of you who don't will no doubt be eager to get on my case... :twisted:

---

### Post by Billy Pilgrim on 2006-11-11
Thanks to mac_an_ultaigh for this post.  I am a computer professional, and have been in the field 30+ years, too.  I understand how hard it is to get an answer in "syntax".

Thanks for everyone else responding, too.  I am wiser than I was yesterday, and the day before.

I saved this to my folder /Ubuntu_Resources for later reference.

---

### Post by mac_an_ultaigh on 2006-11-26
> **Billy Pilgrim said:**
>  Thanks to mac_an_ultaigh for this post. Pleased you found it useful. Thanks for letting me know. :)

---

