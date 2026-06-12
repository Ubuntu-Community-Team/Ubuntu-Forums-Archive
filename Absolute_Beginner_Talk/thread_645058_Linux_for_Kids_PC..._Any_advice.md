---
title: "Linux for Kids PC... Any advice?"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Linux Daddy on 2007-12-19
I'm giving an old  Linux PC to my kids for x-mas. They are 8, 2, and 1. Here is what I have done so far:

1. Installed gutsy
2. Configured VNC for remote administration
3. Set up automatic login
4. Set up automatic wi-fi login
5. Installed multi media codecs

Do you have any suggestions of anything else I should do before giving them the computer? 

Thanks

---

### Post by mmb1 on 2007-12-19
You could install a few kid friendly applications, like tux paint, and install a few extra games.

How computer literate are your kids?

---

### Post by maybeway36 on 2007-12-19
Put icons on the desktop that say stuff like "Web Browser" or "Solitare".

---

### Post by NateMan on 2007-12-19
I'd install the kde desktop, not to use but just to install kdegames package. My girlfriend loves having almost every office game at her fingers. I'd also deffiently add some paint applications. Those were hours of fun at that age. (I guess they still are, I've just moved up to more advanced painting)

---

### Post by mmb1 on 2007-12-19
Like maybeway36 pointed out, you may want to make things a bit simpler than they would be with a default install depending on your kids' experience.

---

### Post by Linux Daddy on 2007-12-19
> **mmb1 said:**
> You could install a few kid friendly applications, like tux paint, and install a few extra games.

How computer literate are your kids?

Good idea thanks!

My 8 year old can browse the internet and print things. My 2 and 1 year old just like to pound on the keyboard and hear sounds. They also like to watch DVDs . My two year old likes to watch me play Tremulous :-)

---

### Post by dfreer on 2007-12-19
All I can currently think of is to make sure their automatic login account can't use sudo. That way they can't accidently delete the OS or something.

---

### Post by Linux Daddy on 2007-12-19
> **NateMan said:**
> I'd install the kde desktop, not to use but just to install kdegames package. My girlfriend loves having almost every office game at her fingers. I'd also deffiently add some paint applications. Those were hours of fun at that age. (I guess they still are, I've just moved up to more advanced painting)

Is KDE easier to use for Kids than gnome?

---

### Post by fatality_uk on 2007-12-19
[http://www.edubuntu.org/]("http://www.edubuntu.org/")

---

### Post by mmb1 on 2007-12-19
I think KDE might be slightly easier if they've been using Windows, but if this is their first OS I'd reccomend letting them use Gnome.

---

### Post by Linux Daddy on 2007-12-19
> **fatality_uk said:**
> [http://www.edubuntu.org/]("http://www.edubuntu.org/")

That's a great idea Fatality. I'm searching the forums for  how to upgrade from Ubuntu to Edubuntu. Thanks!

---

### Post by mmb1 on 2007-12-19
You don't technically have to install KDE to get the kdegames package, do you?

---

### Post by Ex-windows on 2007-12-19
You could install some educational games for the them as well. Seem I saw several these while looking for supertux

---

### Post by thelatinist on 2007-12-19
I would really thin out the Applications menu.  They probably don't need things like Disk Usage Analyser, etc.  No reason they should have terminal either.  You should also remove almost everything from the System menu (they don't need to edit paritions or change the drivers, after all.  And some of that stuff is dangerous if you've got a two year old banging on it).

I second everyone's suggestion of installing extra games and kid-friendly apps.  You might want to check out what Edubuntu installs by default, to get an idea.  Actually...why not install Edubuntu?

---

### Post by Linux Daddy on 2007-12-19
> **thelatinist said:**
> I would really thin out the Applications menu.  They probably don't need things like Disk Usage Analyser, etc.  No reason they should have terminal either.  You should also remove almost everything from the System menu (they don't need to edit paritions or change the drivers, after all.  And some of that stuff is dangerous if you've got a two year old banging on it).

I second everyone's suggestion of installing extra games and kid-friendly apps.  You might want to check out what Edubuntu installs by default, to get an idea.

Do you know if you can upgrade to Edubuntu from Ubuntu? I know you can do it for Xubuntu and Kubuntu but not sure about Edubuntu. 

Do you have access to the same repositories as Ubuntu in Edubuntu?

---

### Post by thelatinist on 2007-12-19
> **Linux Daddy said:**
> Do you know if you can upgrade to Edubuntu from Ubuntu? I know you can do it for Xubuntu and Kubuntu but not sure about Edubuntu. 

Do you have access to the same repositories as Ubuntu in Edubuntu?

I would think you can use:

```
sudo apt-get install edubuntu-desktop
```

Yeah, Edubuntu is just ubuntu with a different set of default apps and settings.  Repositories should be the same.

---

### Post by Duck2006 on 2007-12-19
> That's a great idea Fatality. I'm searching the forums for how to upgrade from Ubuntu to Edubuntu

You can get the packs from your synaptic package manager, look for edubuntu packs.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-12-19
Don't make it completely fool prof you would like it if your 8 year old knows whats going on with a computer right
I mean theres nothing worse then being on a locked down computer
that way if theres a problem he can figure it out for him self
I new more about the computer then my dad did when i was younger maybe not 8 or 9 but defiantly by the time i was 12
btw i was born in 86 so you can figure out what i was exposed to from that and never would have got to linux if my dad had locked up the computer on me :)

---

### Post by Linux Daddy on 2007-12-19
> **<<joe>> said:**
> Don't make it completely fool prof you would like it if your 8 year old knows whats going on with a computer right
I mean theres nothing worse then being on a locked down computer
that way if theres a problem he can figure it out for him self
I new more about the computer then my dad did when i was younger maybe not 8 or 9 but defiantly by the time i was 12
btw i was born in 86 so you can figure out what i was exposed to from that and never would have got to linux if my dad had locked up the computer on me :)

Good point! I want them to learn how to use a computer. To me that means being able to solve minor problems. My 8 year old likes to tinker with stuff so I plan on making it hard to break but not impossible. 

I'm sure I will have to reinstall stuff and repair things. I'm kinda looking forward to that.

---

### Post by NateMan on 2007-12-19
I wasn't suggesting kde for the main windows manager, just installing it so that you can install the kde games package. this package contains a TON of fun little office games. They all run very nicly in gnome :). I'd also try the edubuntu out as well. I would imagine that kde games would need the kde packages since they are designed to run nativly in kde. they would need the packages that kde uses. same as when I use kdevelop in gnome. if it wasn't for kdevelop I probably never would have installed kde.

---

### Post by WarMonkey on 2007-12-19
Install a snes emulator like zsnes ([www.zsnes.com/](www.zsnes.com/)). Don't forget to get roms too.

---

### Post by NateMan on 2007-12-19
I almost forgot, check out neverball and neverputt. two of the most awesome linux time wasters.

---

### Post by g2g591 on 2007-12-19
I was on a PC at age 4. I installed linux (Kubuntu) and my parents didn't even notice for about 4 months. Let them have seperate users, but enable passwordless login (except you, and perhaps the 8 yearold) so they can have seperate Desktops ( I can just see the young kids deleting all the icons)

---

### Post by floke on 2007-12-19
My son (4) loves frozenbubble + Kasteroids + Tuxracer + that gnome breakout game etc. - and he also likes to choose his DE from either KDE, Gnome, or Enlightenment - so make sure they have a choice!

---

### Post by Niniel on 2007-12-19
I have an MS Fingerprint reader, picked it up for 10 bucks a while ago, and my 6 year old loves to log into his own account  using his finger [he got to pick his own background picture, and can click the icons I've placed on the desktop for him; beyond that he doesn't really have much interest yet in exploring the computer]. That's on Windows though, not sure if it'll work with Linux. Might be worth looking into though, children seem to be getting a big kick out of it.

A nice program for kids (boys) is Tonka construction [not sure about the actual name], but again, that's a Windoze software so you'd have to try to get it to work with Wine.

---

### Post by SonicChao on 2007-12-19
I am almost completely positive you don't need KDE to use the kdegames package.

(Not that I don't support KDE ;D I use it 90% of the time I boot into Ubuntu. But you seem to like Gnome better, and it is more user friendly, so definitely better in this situation)

---

### Post by maybeway36 on 2007-12-19
For Edubuntu, you have to delete your kid's hidden settings files so they can regenerate based on the Edubuntu versions. Log in and:
```
mv .gnome2 old.gnome2
```
And most of the kdegames are the same as the gnome-games, but they each have their own exclusives too :)

---

### Post by Seidojohn on 2007-12-19
One of the games I loved as a kid was Super Solvers: Gizmos & Gadgets. Not only did I have a great time playing it, but all of the puzzles you have to solve teach you about mechanics, electricity, magnetism, etc. Here's the description from a games site:    

"Morty Maxwell, the Master of Mischief, has moved into the Shady Glen Technology Center and taken over as the head scientist! Your job is to accept Morty's challenge and prove that you are a better scientist than he is. Morty has locked the doors in the warehouse with science puzzles. Show him how much you know about science by solving the puzzles. Then go through the doors, find the best vehicle parts, and build faster vehicles than Morty builds. To make your job more difficult, Morty's sneaky Cyber Chimps are collecting vehicle parts, too. Outsmart the Chimps by throwing bananas to them and making them take a nap. Race against Morty and win all 15 of the challenge races. You will reclaim the Technology Center and be the head scientist!"

I don't mean for that to be an advertisement, I just really enjoyed the game, and I feel that it helped me cultivate my enjoyment of the sciences.  The game is for DOS, but I know it runs with DosBox (I set it up on a Kubuntu box for my little brother). The puzzles start out really easy, but build in complexity at a good rate.

---

### Post by NateMan on 2007-12-19
well I'm not sure. I already had it installed for kdevelop. I imagine that if it doesn't need kde it probably just installs the needed packages for kdegames. I say if there is diskspace install it anyway. Kids might break gnome, if they are learning :D. the enlightenment idea sounded good too. I still think gnome would be the best desktop though...

---

### Post by Espreon on 2007-12-19
Maybe throw Celestia and Stellarium. And if your 8 year old likes strategy games (and if the comp has decent specs) try throwing on Battle for Wesnoth (not one of those 3D games which require really good hardware). pouetChess is a good chess game (but it might not work on this older PC of which you speak of).

---

### Post by discoade on 2007-12-19
> **Linux Daddy said:**
> Good point! I want them to learn how to use a computer. To me that means being able to solve minor problems. My 8 year old likes to tinker with stuff so I plan on making it hard to break but not impossible. 

I'm sure I will have to reinstall stuff and repair things. I'm kinda looking forward to that.

Thats the spirit! i mean how long does it take to do a reinstall! minutes these days! as long as its not your main pc let em get on with it! its the way i learnt.

god knows how many times if redone the kids xp pc! but its all fun! now my 13 year old comes down and says " dad its busted again!" so i have a look "yep its busted! go on reinstall!" and he does!  13 and he can install xp! including reformatting! i'll soon be obsolete!

---

### Post by Moop on 2007-12-19
My 5 yr old granddaughter has been using Ubuntu for a couple years. Gcompris & Childsplay are two of the programs she likes. Debian has some great kids programs. 

Do a search in Synaptic with the key word children.

---

