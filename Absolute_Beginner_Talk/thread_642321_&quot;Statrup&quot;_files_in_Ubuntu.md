---
title: "&quot;Statrup&quot; files in Ubuntu?"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by rondamato on 2007-12-16
Hello,

I want to invoke compiz on my box using a switch that improves the performance of NVidia cards pretty well...it's done like so: 

I was told to try:
compiz --replace --loose-binding

It sped up my gfx operations in compiz dramatically.  I asked if anyone knew how I could invoke compiz with this switch every time I logged into my WM--especially since Gutsy's GDM has a CP for compiz at SYSTEM>PREFERENCES>ADVANCED DESKTOP EFFECTS SETTINGS.  Would it screw up my compiz prefs or run two instances if I autorun this command upon startup?  I ran it a few times in a term and, after some vidprobing, all was well--just faster.

I asked the Community how to autorun this command upon GDM start and I was answered:

>>I'm not an expert but if i remember corectly ubuntu launches compiz through a script >>called compiz.real or someting similar.
>>try looking in that script and adding the switch there.

Good advice.  Alas, I tried to vi /usr/bin/compiz.real and it is a binary file, not a conf file as I also would have thought.

This is a STOOOPID question, but I must ask it. Is there a place where I can put a path to a file to be executed at the startup of my window manager? I use Gnome. I know how to do this in BSD but it seems to be different in Ubuntu. Plus the code I want to execute is compiz with the "loose-bindings" switch. Normally Compiz starts with the WM and its CP is accessed thru SYSTEM>PREFERENCES>ADVANCED DESKTOP EFFECTS SETTINGS. I can open a term and run the command at a shellprompt and all is well. I just want to automate this! Will I have to change anything in the "official" Compiz CP in Gnome/Ubuntu (Gibbon)?

So, for the Windoze folks out there I'll put it like this--does Ubuntu have something like Windows' "Startup" folder where anything in it will be run at startup? Or something like a win.ini where I can say [run=x]?

Also, if there is (and I KNOW there IS) a file where these conf args go, does it just affect the logged-in user or global users?  I'd bet that depends on WHAT FILE you use, knowing UNIX, right?  So...what files DO I use?  I actually AM experienced with UNIX--mostly Solaris and BSD, but Ubuntu does some things differently (and any differences are WAAAAY for the better).  I love this OS.  I try to get my customers to adopt but "Linux" (the word) is like saying "serial killer" to most of them.  They picture a PC with no monitor and millions of LEDs on the front blinking with a geek with an everpresent belt-mounted HP-41C running it all...  

Still, "our" OS of choice is orders of magnitude better than Vista, XP, or even Leopard.  When I show people (of course they are all Windows users) what I can do and DO do every day--including having compiz running (which is no really big deal) they tell me that it "must be a video" because their dual-processor, quad-core, 4GB, 1033MHz FSB, SATA-RAID-equipped Vista Ultimate Direct X 10 machine cant do that stuff so smoothly--and that  while running three monitors, Firefox, a system monitor, Skype, indexing a drive, playing an mp3, playing Quake AND doing compiz trix simultaneously is NOT POSSIBLE.  I just smile and remind them that its a FREE OS running FREE APPS.  If I can get as far as committing them to an fdisk then they never, ever go back to Windows.  Thought this anectdote might make someone smile.

Once I understand this thing with file locations and confs my Ubuntu knowledge will go up <300% (seriously) so anyone who takes the time to read this and answer is a damn cool person in my book!


Thank you so much!

Ron

---

### Post by aeiah on 2007-12-16
you could add your compiz command to system>preferences>sessions. because you're using the --replace tag, it will replace your normally running compiz (or whatever else you have running, such as metacity). this would be more elegant if you dont have ubuntu load the normal compiz on startup at all of course, which im guessing can be done through the compiz preference menu you mentioned. im not sure, because ive only just moved to gutsy from previous versions of ubuntu, and in those it was always done through a sessions start up command

---

