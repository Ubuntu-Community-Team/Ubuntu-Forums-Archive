---
title: "frostwire wont connect"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by Linux&amp;Lizards on 2006-11-04
ok guys here goes.
i just finished installing frostwire via automatix and i also finished updating my computer.
now my frostwire wont connect, i dont think it was the update that is stopping it because it didnt connect before that.
any how i know this is a hot topic and i eagerly await your replies!

---

### Post by Linux&amp;Lizards on 2006-11-04
im trying to reinstall frostwire to see if that is the problem:rolleyes:

---

### Post by blendmaster on 2006-11-04
See this link: [http://www.ubuntuforums.org/showthread.php?t=292463]("http://www.ubuntuforums.org/showthread.php?t=292463")

That's if you already had it working ut it says starting connection forever.

---

### Post by Linux&amp;Lizards on 2006-11-04
> **blendmaster said:**
> See this link: [http://www.ubuntuforums.org/showthread.php?t=292463]("http://www.ubuntuforums.org/showthread.php?t=292463")

That's if you already had it working ut it says starting connection forever.

i tried that i was there when you made your discovery.
but it wont connect even when i do restore is.
did i mention that i am using dapper?
and im kinda new so please excuse me for asking boring questions.

---

### Post by blendmaster on 2006-11-04
Hmm...

Well, you didn't install any firewalls I'm guessing, right?

Did you accidentally set it up to work through a SOCKS or HTTP proxy?

Go to settings and make sure that's not the problem.

---

### Post by Linux&amp;Lizards on 2006-11-04
> **blendmaster said:**
> Hmm...

Well, you didn't install any firewalls I'm guessing, right?

Did you accidentally set it up to work through a SOCKS or HTTP proxy?

Go to settings and make sure that's not the problem.

how would i check the settings?
i know i didnt set it upp for a proxy.
but it says it detected a firewall
how would i check the settigs? 
would i click on options?

---

### Post by Linux&amp;Lizards on 2006-11-04
> **Linux&Lizards said:**
> how would i check the settings?
i know i didnt set it upp for a proxy.
but it says it detected a firewall
how would i check the settigs? 
would i click on options?

hey it says it has an exellent connection!
i wonder what is going on i took a shower and now it says it is good so i guess im good........for now anyways.
ty for the help ill pm you if i need further assistance.

---

### Post by blendmaster on 2006-11-04
> hey it says it has an exellent connection!
i wonder what is going on i took a shower and now it says it is good so i guess im good........for now anyways.
ty for the help ill pm you if i need further assistance.

Hey, that's awesome!

It's great that you got it going, and I don't know why Frostwire is like this.

I think it's a bug with the latest version or something, because this keeps popping up. It will claim it's behind a firewall, even if it's not really.

I hope that it's a minor bug, and that other people will find a solution (however weird it may be...)

---

### Post by Linux&amp;Lizards on 2006-11-04
> **blendmaster said:**
> Hey, that's awesome!

It's great that you got it going, and I don't know why Frostwire is like this.

I think it's a bug with the latest version or something, because this keeps popping up. It will claim it's behind a firewall, even if it's not really.

I hope that it's a minor bug, and that other people will find a solution (however weird it may be...)

i agree this is just bazar!

---

### Post by jeff1968 on 2006-11-04
Can you give me some direction how did you check "firewall"

Thanks

---

### Post by xpod on 2006-11-04
Hey guys...my frostwire is in a permenant "starting connection" state too.

Both on dapper & on edgy?
It usually works fine even with the firewall?

---

### Post by jso2897 on 2006-11-04
I'm having the same problem. And so far, it hasn't "fixed itself" as it seems to for a couple of folks. I've got Frostwire set to PnP firewall configuration, and I checked my router - it's set up for PnP. I have no software firewall. My router serves three other computers, all working fine. This computer ran Frostwire thru the same port in the same router when it was a Windows box - no problem. It's driving me nuts - I hope somebody figgers something out - I got nothin' at this point.](*,)

---

### Post by blendmaster on 2006-11-04
It seems the Frostwire Forums seem to have another "This may work..." solution [here]("http://www.frostwire.com/forum/viewtopic.php?t=652").

I haven't tried it though...

---

### Post by xpod on 2006-11-04
Well ive tried opening the "ftp 20-21 port" but that never made any difference and im not sure about the other "netbios" one....Dont know why it would matter though as it`s always worked fine before....

Anyway, im not too sure about any of it...Im only just learning about the "paths" within an os\pc and im afraid the specific "ports" in or out of it are still a bit beyond my very limited knowlage at the moment.:confused: 

I`ll leave mine for now as bed beckons but we`ve got a second internet connection so im going to check it on that tommorow if it still aint playing ball here on this one...just out of curiosity.

Goodnight and good luck....Hopefully i`ll have frostie`s by breakfast;)

---

### Post by veli on 2006-11-04
I had the same problem with "no connection" in Frostwire. After a long time to have it installed and loaded, I gave it up. I found the solution of my problem, it's called Gtk-Gnutella, as one of the forum fellows suggested it as an alternative of Lime/frostwire. It's GTK based, small, eat no resourses, and works perfectly in Edgy. Give it a try, if you don't have any specific reason to use Frostwire. AFAIK, Frostwire is within the Gnutella network, isn't it?

---

### Post by jso2897 on 2006-11-04
Success! I went into Frostfire's options/advanced/firewall config, and set the two ports to 6346. I was going to configure my router, but never had to -I happened to idly restore Frostwire before I did that, and saw that it had connected! This is wierd - something a little different is happening to everybody with this issues.:-k

---

### Post by blendmaster on 2006-11-04
I know!

It seems to be a bug in the latest version of Linux Frostwire.

I wonder if it happens with Windows and Mac versions?

Either way, someone should contact them regarding this issue, as I don't know when the next version will be released.

---

### Post by Dual Cortex on 2006-11-04
Even if your router supports UPnP, just open your ports through your router's interface.

---

### Post by jso2897 on 2006-11-04
Now it gets wierder. I messed around and clicked too many buttons, and froze up the Frostwire GUI. So i booted, started it again, and again it stays at "starting connection". But the file I was downloading started to download again, and is currently downloading from 7 hosts @ 37kbs (which aint bad on my lowline DSL). Even though it says "starting connection". And STILL shows the stoopid little brick firewall icon.](*,) 

Oh well, it's working. I guess I should quit snivelling.:D

---

### Post by Dual Cortex on 2006-11-04
Is your Router well configured with your DSL modem?
I was having a somewhat similar problem as you did... except it was with Windows XP and uTorrent.
I eventually figured out that my Router was not well configured with my modem when trying to set up an FTP server.

I had just plugged in my my router to my modem... some programs were able to access the internet while some weren't. And some ports reported not being able to connect while they were actually connected.

---

### Post by jso2897 on 2006-11-04
Yes. I have thre other computers running off the router and dsl modem - everything works fine. Frostwire worked fine on this same computer and in the same port on the same router - but I am having this same issue. It's back now. I'm giving up now, for a while. I'll go check out the Frostwire forums.:-k

---

### Post by jso2897 on 2006-11-04
OK. Actually, that was very informative. The Frostwire forum is full of PAGES of posts of the same complaint. Seems to have started about a week ago, and affects windows users too, not just us.

---

### Post by Linux&amp;Lizards on 2006-11-04
hey jeff i didnt.
when you open frostwire your firewall icon should be to the >right> of your connection status.
unfurtunatly i dont think that a firewall is are problem.
i had the same problem as you and i restarted my computer, repluged my internet cord and left it alone.
i dont know what to tell you because i am so inexperianced sry.

---

### Post by jeff1968 on 2006-11-04
Thanks for your help .......... I will wait and see what tomorrow brings

---

### Post by xpod on 2006-11-05
Good morning folks...still no frosties then.
Ive tried the 6346 fix suggested but that did`nt have no effect either.Even checked things out on my other connection and its the same on that...SO i know it`s not just me this time:

Anyway, ive took Feli`s advice and had a wee look at gtk-guntella,Which im happy to say works fine..
Thats not to say i`ll be giving Frostwire the cold shoulder....It would just annoy me if i was to leave it:twisted

Good luck the rest of you`se....

---

### Post by jeff1968 on 2006-11-05
XPOD

How do you get that program?  ... sorry ... I am a newbie

Thanks

---

### Post by bulldog on 2006-11-05
Type GTK-Gnutella in the search box of your synaptic.

---

### Post by jeff1968 on 2006-11-05
Hi Bulldog

I tried and it did not find that package?  Do I have to download from somewhere?

Thanks

---

### Post by bulldog on 2006-11-05
Do you have universe and multiverse repositories enabled?

---

### Post by jeff1968 on 2006-11-05
Bulldog

Longtime windows user .... Ubuntu is all new to me .... could you help me step by step to check out what you have asked

Thanks

---

### Post by bulldog on 2006-11-05
Yep I could do that :D 

I presume you can start synaptic and take it from there.
I have to say I use a dutch version,so I could say the wrong tab names.

Well if synaptic is open go to the Preferences tab [fourth]and look for the second option in there which allows you to enable your repositories.

Enable them all and push the reload button on the left of the mainbar.

Look again for GTK-Gnutella.

---

### Post by jeff1968 on 2006-11-05
Hi

I found the preference tab and the repositories tab but no option to enable ............ any help or I will just have to move on

Thanks

---

### Post by bulldog on 2006-11-05
Another way to do it then.```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```
To backup the list for safety.:D 

Then ```
sudo gedit /etc/apt/sources.list
```which will open your sources.list in a text editor.

Now uncomment the Universe and Multiverse repo's[uncomment is removing the # before the repo-line's]

If done save the file and close it and update synaptic```
sudo aptitude update
```

Try again to see if the Gnutella package is available to you.

---

### Post by jeff1968 on 2006-11-05
Thanks Bulldog ..... got it working

This is why I switched from windows ..... wanted to learn a system ... these forums are a great resource .... if you find a fix for Frostwire please send me a message

Thanks again for your patience

---

### Post by bulldog on 2006-11-05
No problem.........:D

---

### Post by Linux&amp;Lizards on 2006-11-05
i agree these forums rock!

---

### Post by jso2897 on 2006-11-05
I gave up in disgust, and tried gtk-gnutella (it's in my apps. to install list). Works great, does everything Frostwire does and is much thinner. It only uses about a fifth of the cpu and ram on my machine that frostwire does. Or I should say, did, as I have uninstalled Frostwire and am in the process of blotting out my memory of this nightmare. Best thing is, this app is supported within the Ubuntu community. The support available in the Frostwire community is.....well....let's just say I went there, and the response that the pages full of posters complaining about this are getting is:
1. Fanboy tells poster he is having problems because he purchased his Frostwire from a scam outfit (usually not applicable, and not true in any case - the version the scammers are selling is identical to the "real" one, which is also broken))
2. Fanboy insists Frostwire is all just hunky-dory, and poster is having problems because he is a stupid noob who hasn't read some (also inapplicable and inaccurate) sticky post.
3. Fanboy states that he has a simple, easy solution that works across all platforms, for everybody. Only, he won't discuss it in the forums. He will only discuss in in private chat. WTF?!?!?!
](*,) 
Anyway, I got gtk-gnutella, it's better anyway, forget 'em.
The best thing about Ubuntu is the real, quality support community. Without that, the best app in the world is worthless - at least in the opensource world.

---

### Post by Linux&amp;Lizards on 2006-11-05
Way to go! you sure nailed that one on the head.
I myself took a little stroll down to their forums yesterday and recieved some pretty bitter treatment.
i dont know if im going to give upp frosty just yet but i have gtk gnutella if thing run really sour.
I dont have much faith in fosty i just got it a week ago and i must say their community is to say the least and the most politely LACKING!
:rolleyes:  well i guess we are you spoiled because we have these great ubuntu forums, even when people are rude here its not nearly the same as when someone is trashing you on the mepis forums those guys can just get honery.
did i spell honery right?
i think i didnt, well anyway i agree the unbuntu forums rock!

---

### Post by Midway on 2006-11-05
I have to agree, the FW people on their forums do lack social skills.  I will just use GTK-Gnutella for now.

BTW, it is "ornery" :mrgreen: 

ornery
     adj : having a difficult and contrary disposition; "a cantankerous and venomous-tongued old lady"- Dorothy Sayers [syn: {cantankerous}, {crotchety}]

---

### Post by Linux&amp;Lizards on 2006-11-05
kk ty lol :)

---

### Post by jso2897 on 2006-11-05
Linux & Lizards: To help you make up your mind, I suggest you try something. Load up gtk-gnutella (it loads right from add/remove programs) and just run it. don't worry about configurating you router or anything - just run it, and check your system stats. Then do the same thing with Frostwire, noting how much resource each app uses. I think you'll see what I mean.

---

### Post by blendmaster on 2006-11-05
I agree, these forums are the best that I have ever been to!

And I think that switching to GTK-Gnutella might be a good idea for the moment.

That's not to say that Frostwire is a bad program, but I think that we can't wait for the next version release to have all of this fixed. (and yes it is resource hungry, I've had to restart my computer because of it a couple of times already).

In the meantime, I think we can enjoy the awesome forums that we have right here! ;)

---

### Post by Linux&amp;Lizards on 2006-11-05
I agree that was well said.
gtg I have to go move bedrooms around today!

---

### Post by zappa420 on 2006-11-06
you need to replace gnutella.net

its located here:
/home/[USERNAME]/.frostwire/gnutella.net

replace it with this one:
[http://mc3.electronicbox.net/gnutella.net]("http://mc3.electronicbox.net/gnutella.net")

its just peer ip addresses so you can just cut and paste it.

this is the link I got the info from.
[http://www.frostwire.com/forum/viewtopic.php?t=666&postdays=0&postorder=asc&&start=15]("http://www.frostwire.com/forum/viewtopic.php?t=666&postdays=0&postorder=asc&&start=15")

i hope that works for you too

---

### Post by blendmaster on 2006-11-06
> you need to replace gnutella.net

its located here:
/home/[USERNAME]/.frostwire/gnutella.net

replace it with this one:
[http://mc3.electronicbox.net/gnutella.net](http://mc3.electronicbox.net/gnutella.net)

its just peer ip addresses so you can just cut and paste it.

this is the link I got the info from.
[http://www.frostwire.com/forum/viewtopic.php?t=666&postdays=0&postorder=asc&&star](http://www.frostwire.com/forum/viewtopic.php?t=666&postdays=0&postorder=asc&&star) t=15

i hope that works for you too

Can anyone confirm this?

If so, then the solution should really be stickied somewhere, as this is an extremely common problem.

I would test it, but it wouldn't really help considering my connection already works (and I don't want to mess anything else up).

Thank you zappa420 for the suggestion, we'll have to wait for someone to come along and test this out (not that I don't trust you, but what works for a couple people might not work for everyone).

Thanks!

---

### Post by Linux&amp;Lizards on 2006-11-06
how do i excess the fle and replace it?

---

### Post by blendmaster on 2006-11-06
Edit: Never mind! I forgot about hidden files...

---

### Post by Midway on 2006-11-06
It is there, you have to show hidden files to see it.

I opened the file and it lists a bunch of addresses.  Do you delete these and replace it with the single one mentioned?

EDIT: N/M I see now that it is a link to the addresses to be pasted into this file.

EDIT 2: Ok, just right click on the link and save it.  Then use it to replace the original.

---

### Post by Midway on 2006-11-06
That did it!  I now get Excellent Connection, thanks! :)

---

### Post by blendmaster on 2006-11-06
Sorry, I forgot about the default hidden files thing!

Yeah it's there, and now I really think this should be stickied, it's a great solution!

zappa420, thanks for bringing this to us!

---

### Post by Midway on 2006-11-06
Or at least put in the "Edgy Known Bugs and Workarounds" sticky in General Help.

Well, now that I think about it, Dapper users were having problems too.

---

### Post by lon3lyliv3r on 2006-11-06
wow!

thanks a ton!
that worked perfectly to fix my connection problem!

before i pasted what u said there was about 10 lines...

anyone know why this fixes it?


thanks again!
john!

---

### Post by Linux&amp;Lizards on 2006-11-06
what do you clik to open the file?

---

### Post by et voilà on 2006-11-06
Salut ubuntuforums users :) FW wasn't connecting because host caches used by default in the gnutella.net of FW 4.10  are not working anymore. The temporary solution is to update the list with working host caches. A host cache is server that upon request, sends IP : port of stable Gnutella nodes so you can connect when you first install FW or when no known Gnutella nodes respond to connection request.

FW should release a new version soon to overcome this problem.

Still, advanced users who have a good computer, plenty of bandwidth, on the net 24/24 and want to help the Gnutella network should set a UHC (UDP host cache) on their computers. That way Gnutella will have stable bootstrap caches for the future. Right now, there are too few caches to support Gnutella growth and stability. This will help all clients on Gnet and Linux is the best OS to host those caches. For more information see [http://ghostwhitecrab.com/crab/](http://ghostwhitecrab.com/crab/)

Ciao and happy sharing!

---

### Post by blendmaster on 2006-11-06
Click Places >> Computer

Double Click Filesystem >> home >> <username>

Click View >> Show Hidden Files (or hit CTRL-H).

Now find .frostwire and double click it.

Double Click gnutella.net and copy and paste over the files contents with the one on the link.

---

### Post by Linux&amp;Lizards on 2006-11-06
um guys how do i find, open, and replace the file you are alking about?

---

### Post by Midway on 2006-11-06
I just dragged the downloaded file into the .Frostwire folder and answered yes to replacing the original file.  Either way will work.

---

### Post by blendmaster on 2006-11-06
> I just dragged the downloaded file into the .Frostwire folder and answered yes to replacing the original file. Either way will work.

Lol. I tend to do things the hard way, don't I? :-D

---

### Post by Linux&amp;Lizards on 2006-11-06
so then it should look like these?

---

### Post by Midway on 2006-11-06
> **et voilà said:**
> Salut ubuntuforums users :) FW wasn't connecting because host caches used by default in the gnutella.net of FW 4.10  are not working anymore. The temporary solution is to update the list with working host caches. A host cache is server that upon request, sends IP : port of stable Gnutella nodes so you can connect when you first install FW or when no known Gnutella nodes respond to connection request.

FW should release a new version soon to overcome this problem.

Still, advanced users who have a good computer, plenty of bandwidth, on the net 24/24 and want to help the Gnutella network should set a UHC (UDP host cache) on their computers. That way Gnutella will have stable bootstrap caches for the future. Right now, there are too few caches to support Gnutella growth and stability. This will help all clients on Gnet and Linux is the best OS to host those caches. For more information see [http://ghostwhitecrab.com/crab/](http://ghostwhitecrab.com/crab/)

Ciao and happy sharing!

Merci! 

I wish I could help out but I am on satellite internet that has a limited bandwidth per month :(  But I definitely agree with this statement "This will help all clients on Gnet and Linux is the best OS to host those caches." :mrgreen:

---

### Post by Linux&amp;Lizards on 2006-11-06
so then blender did i do it right?

---

### Post by Linux&amp;Lizards on 2006-11-06
it still says starting connection

---

### Post by blendmaster on 2006-11-06
Hang on. I have screenshots coming.

---

### Post by Midway on 2006-11-06
> **Linux&Lizards said:**
> so then it should look like these?

No, though that is what I thought the poster meant at first.

The link the poster supplied is a link to a file.  Just right click on the link and download the file on your desktop.  Then open up .frostwire and then drag the downloaded file into the .frostwire window.  It will ask you if you want to replace the original file and say yes.

---

### Post by Linux&amp;Lizards on 2006-11-06
ooooooooooh ok ill try that and then get back to you :)

---

### Post by blendmaster on 2006-11-06
The first screenshot (screenshot.png) shows the file link. Right click it, and click file save as, and then save (screenshot-1.png). After it's done (screenshot-2.png), you'll see a file on your desktop (screenshot-3.png). Open the .frostwire folder (use my previous steps) and drag the downloaded  file to the folder (screenshot-4.png). Tell it you want to replace, and you should be good.

---

### Post by Midway on 2006-11-06
LOL, I was just working on something like this, Blender.

The effect is instantaneous, I had forgotten I had left FW on and when I maximized it I saw "Excellent Connection".

---

### Post by Linux&amp;Lizards on 2006-11-06
1 sec im still workn on it

---

### Post by Linux&amp;Lizards on 2006-11-06
well ive done those steps and reinstalled frostwire to no avail so i guess im just gona have to 8 dang it!
are you guys usin edgy?
im using dapper if it has anything to do with it?

---

### Post by blendmaster on 2006-11-06
Hmm... I guess everyone who's claimed this to work has been using Edgy (at least, according to their profiles...)

I don't know why it would be distro specific though, mainly because it's an independent program.

Well, I guess this is yet **another** solution that may or may not work depending on the situation.

Oh well. I really hope for yours and others sakes that this gets fixed, but I guess there's always GTK-Gnutella for now...

Sorry I can't help very much more...

---

### Post by Midway on 2006-11-06
The problem was not distro related or even OS related as I have seen Windows posters having the same problems.  From the Viola! post above it was a FW problem of using outdated sources.

I do not know why you can't get it to work, the fix is relatively simple, just replacing a source list :confused:

---

### Post by Midway on 2006-11-06
> **blendmaster said:**
> Hmm... I guess everyone who's claimed this to work has been using Edgy (at least, according to their profiles...)

I don't know why it would be distro specific though, mainly because it's an independent program.

Well, I guess this is yet **another** solution that may or may not work depending on the situation.

Oh well. I really hope for yours and others sakes that this gets fixed, but I guess there's always GTK-Gnutella for now...

Sorry I can't help very much more...

I would like to see other Dapper users try this and report their results as well.  It doesn't make sense why it would only work for Edgy if the problem was only outdated sources.

Of course even though I have been using Linux only a couple of years and there is alot I don't know what goes on "under the hood" so this might fall into that category.

---

### Post by David Corrales on 2006-11-07
I can confirm the new gnutella.net fix works :)

---

### Post by billybag on 2006-11-07
I am pleased to announce, that after hours of searching, the gnutella.net thing worked for me.
i am not using edgy.
Ubuntu Linux Breezy Badger 5.10

just to clearify. This was my problem:
I would open up frostwire and the program would remain stuck on "starting connection" and next to that would be the icon indicating that a firewall was detected.

i saved the gnutella.net to my desktop. I then went into Places>Computer> /Filesystem/Home/myusername/.frostwire (note you have to choose the "show hidden files" option in the VIEW MENU in order to see this folder) i then dragged the gnutella.net file (the one i saved on my desktop) into the .frostwire folder. It asked me if i wanted to replace the file already named gnutella.net that was already in the .frostwire folder. i clicked YES to confirm i wanted to replace it. I then started frostwire up and it works fine now. i hope this helps!

---

### Post by Linux&amp;Lizards on 2006-11-07
delete

---

### Post by guliver on 2006-11-07
For people who still have troubles here is a guide:

- Turn off Frostwire by right clicking its icon on taskbar and select Exit

- Delete gnutella.net file located at /home/yourusername/.frostwire/

- Download new file located here [http://mc3.electronicbox.net/gnutella.net](http://mc3.electronicbox.net/gnutella.net)

- Save it on desktop and simply drag to .frostwire folder.

/.frostwire folder is hidden and you can open it by Nautilus and from View many select "Show hidden files"

-  path th the folder again /home/yourusername/.frostwire/

**g**nutella.net is the right file name, **G**nutella.net will not work!

---

### Post by Linux&amp;Lizards on 2006-11-10
It works great in dapper!
We did it guys we did it enjoy!

---

### Post by Magnus150 on 2006-11-10
Dapper user here, I can confirm that this new file works perfectly! Just sprung right up once I replaced the old one. Thanks a ton for the solution!

---

### Post by PacShady on 2006-11-11
I tried the gnutella.net file on the link, with the "uhc2.limewire.com:20181,,1162480626164,,,en,0" system of storing caches, but it didn't work for me. My gnutella.net file stores the caches differently, just using the URL for the cache rather than adding all the numbers behind it. So I got the idea of adding new caches to it manually, using just the URL, getting working caches from [http://gcachescan.jonatkins.com](http://gcachescan.jonatkins.com). It's working fine now. Hope that helps anyone.

'Shady

---

### Post by xpod on 2006-11-11
Well i`d forgot all about FW and have been more irritated with amule this last week but thats another story.

Frostwire though is now working fine here in dapper & im sure it`ll be the same in edgy,My "gnutella.net" file was completely empty:-k .... and had nothing in it until i pasted that over.So simple when you know how eh.

All fine now though.
Happy pilfering folks;)

---

### Post by Linux&amp;Lizards on 2006-11-12
This is cool now that it is working.
So tell me do you suppose we should share our discorvery with other forums?

---

### Post by bswilson on 2006-11-17
> **zappa420 said:**
> you need to replace gnutella.net

its located here:
/home/[USERNAME]/.frostwire/gnutella.net

replace it with this one:
[http://mc3.electronicbox.net/gnutella.net]("http://mc3.electronicbox.net/gnutella.net")

its just peer ip addresses so you can just cut and paste it.

this is the link I got the info from.
[http://www.frostwire.com/forum/viewtopic.php?t=666&postdays=0&postorder=asc&&start=15]("http://www.frostwire.com/forum/viewtopic.php?t=666&postdays=0&postorder=asc&&start=15")

i hope that works for you too

[SIZE="3"]One more vote for this solution to be a sticky.  I tried many other posted solutions, but only this worked for me.  Thanks, Ubuntu Forums![/SIZE]

---

### Post by BLTicklemonster on 2006-11-18
replacing .net worked for me on edgy/6.10, too.

---

### Post by needlenose on 2006-11-18
> **blendmaster said:**
> Click Places >> Computer

Double Click Filesystem >> home >> <username>

Click View >> Show Hidden Files (or hit CTRL-H).

Now find .frostwire and double click it.

Double Click gnutella.net and copy and paste over the files contents with the one on the link.

Worked perfect thanks. Edgy/6.10

---

### Post by staib on 2006-11-19
Worked for me too (on Edgy) - bonus too - street cred restored with teen son who was beginning to moan about the move from XP 8) 

Thanks all who contributed in such detail to this solution!

Nick

---

### Post by gubatron on 2006-11-27
[Please upgrade to 4.13.1]("http://peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb")


Info on what's new and how to install here:
[http://www.frostwire.com/blog/2006/11/21/try-frostwire-413-ubuntu-installer-now-with-bittorrent/](http://www.frostwire.com/blog/2006/11/21/try-frostwire-413-ubuntu-installer-now-with-bittorrent/)

---

### Post by Linux&amp;Lizards on 2006-11-27
Ive tried this over and over with other distros suse, pclinuxos, and diff versions of ubuntu.
It works every time I agree that this should be a sticky!

---

### Post by Psquared on 2006-11-27
Interesting. It didn't work at first for me. Briefly it went to "poor connection" and then back to a single bar. I went back to reading the forum in hopes there was another fix and then went back and "viola" I have an excellent connection.

My setup is a little different too. I'm running Kubuntu 6.10 "fresh install" with Frostwire installed using Automatix. Anyway, it does work - at least for now.

Thanks,

---

### Post by Linux&amp;Lizards on 2006-11-28
Automatix makes our life so much easier:)

Is there some way to show our thanks?

---

### Post by sabitha on 2006-12-02
> **gubatron said:**
> [Please upgrade to 4.13.1]("http://peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb")


Info on what's new and how to install here:
[http://www.frostwire.com/blog/2006/11/21/try-frostwire-413-ubuntu-installer-now-with-bittorrent/](http://www.frostwire.com/blog/2006/11/21/try-frostwire-413-ubuntu-installer-now-with-bittorrent/)

i reinstall with this new but still wont connect.
theres something wrong with frostwire or just me ](*,).
i just replace the gnutella.net like on this forum say but wont connect ](*,)

---

### Post by DougieFresh4U on 2006-12-02
And your Java & Flash work? which Java? You don't say what it's doing. Not connecting? Not loading?

---

### Post by tradesman on 2006-12-02
> **gubatron said:**
> [Please upgrade to 4.13.1]("http://peercommons.com/frostwire/4.13.1/frostwire-4.13.1.i586.deb")


Info on what's new and how to install here:
[http://www.frostwire.com/blog/2006/11/21/try-frostwire-413-ubuntu-installer-now-with-bittorrent/](http://www.frostwire.com/blog/2006/11/21/try-frostwire-413-ubuntu-installer-now-with-bittorrent/)

This worked for me thanks:D

---

### Post by Frak on 2006-12-13
[http://ubuntuforums.org/showthread.php?t=315222&highlight=frostwire](http://ubuntuforums.org/showthread.php?t=315222&highlight=frostwire)

---

### Post by rpasell on 2007-02-28
I tried this solution, worked great.

---

### Post by darkmediator on 2007-12-27
I read this thread. Looks promising in resolving my problem. I tried "http://mc3.electronicbox.net/gnutella.net". But it redirects me to "http://360share.com/". I am on fedora 8. I think the file is no longer there.

So anyone who has frostwire connecting perfectly or someone who downloaed that file can please share it here or attach it? :)

---

