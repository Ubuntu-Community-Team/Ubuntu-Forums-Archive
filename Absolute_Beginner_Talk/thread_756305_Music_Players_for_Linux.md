---
title: "Music Players for Linux"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by AeThEr777 on 2008-04-15
I did a search for audio players for linux and found songbird. The only thing that I cant get on Linux is Itunes and ive grown accustomed to itunes over the years, Songbird looks to be just like it and will help me forget about itunes. Anyone use, songbird and like it? Any quick reviews on it, and how to install it if it is good? Thanks

AeThEr777

---

### Post by sonatso on 2008-04-15
My recommendation is to download wine, either from its website at [www.winehq.org]("http://www.winehq.org") or from the Synaptic Package Manager and try to use iTunes if you prefer it. Also, Ubuntu comes with a music player, so you could also use that. As for Songbird, it is free to download at [songbirdnest.com]("http://songbirdnest.com"), though it is a new program, as they warn you on the site, and may have bugs.

---

### Post by tvtech on 2008-04-15
I love amarok for large music databases it's great!  some other people like rythmbox  I'm not some other people.

---

### Post by Frenske on 2008-04-15
I use songbird on Linux, because I did not like the ubuntu default player (whatever that was) but it is not even near iTunes. It is slow to start up and not really responsive; it might be the just the Linux version and I suspect that the Mac is what the developers are mainly using. It plays the songs and it looks good and it feels a bit like iTunes.

Perhaps I make it sound it is a bad program. Considering it is still more or less in the beta phase (version 0.5 was just brought out) it is a capable program. It might be an ugly duckling now but giving the time it might grow in a beautiful swan. ;)

---

### Post by Crafty Kisses on 2008-04-15
I like SongBird, also Rhythmbox is pretty good in itself. You may also want to look into Banshee, it just depends.

---

### Post by AeThEr777 on 2008-04-15
ok i just discovered the add/remove thing application. I found amarok but it says

"Amarok cannot be installed on your computer type (i386) either the application requires special hardware features or the vendor decided to not support your computer type" 

Uh oh what now?

---

### Post by Inxsible on 2008-04-15
Rhythmbox, the default Ubuntu music player is pretty much like iTunes(although it does not have all the features)

Amarok is another, Exaile is yet another, so is Banshee...

Lots of choice...I think you should try out each one of them until you like something that you can live with :D

---

### Post by y-lee on 2008-04-15
> **tvtech said:**
> I love amarok for large music databases it's great!  some other people like rythmbox  I'm not some other people.

Amarok is my choice too tho I have been unable to make it match the theme I use for my gnome desktop. But then again I gave up after a couple hours working one day and that is a minor issue for me anyway.

---

### Post by AeThEr777 on 2008-04-15
Can anyone help with the install problem for Amarok? the error msg is a few posts back! Thanks

---

### Post by Inxsible on 2008-04-15
> **y-lee said:**
> Amarok is my choice too tho I have been unable to make it match the theme I use for my gnome desktop. But then again I gave up after a couple hours working one day and that is a minor issue for me anyway.That is my point of contention too. KDE apps are mostly blue and I have the Human theme going in Ubuntu so it looks kinda odd.

But since I always start it in minimized mode and use my hotkeys..i dont really have to see the app as such !!

---

### Post by Inxsible on 2008-04-15
> **AeThEr777 said:**
> Can anyone help with the install problem for Amarok? the error msg is a few posts back! ThanksAmarok exists for both 32 and 64 bit versions and it should automatically select the appropriate version for your OS. So I am not sure why you are getting that problem.

But have you enabled the proper repositories? I just checked that I have Amarok installed from the Medibuntu repos. You might wanna try those repos.

---

### Post by AeThEr777 on 2008-04-15
lol i have two threads going and these "repos" seem to be entioned alot and are probably the reason im having so mnay problems. I have no idea what they are tho. Can anyone tell me step by step where to go what to check etc. 

AeThEr777

---

### Post by Inxsible on 2008-04-15
> **AeThEr777 said:**
> lol i have two threads going and these "repos" seem to be entioned alot and are probably the reason im having so mnay problems. I have no idea what they are tho. Can anyone tell me step by step where to go what to check etc. 

AeThEr777Repositories or Repos for short are additional source where you can find software that you can install on your machine.

---

### Post by AeThEr777 on 2008-04-15
So im guessing i have them disabled. How do i change that?

AeThEr777

---

### Post by Inxsible on 2008-04-15
> **AeThEr777 said:**
> So im guessing i have them disabled. How do i change that?

AeThEr777System>>Administration>>Software Sources. Check mark the boxes for universe and multiverse.

---

### Post by Inxsible on 2008-04-15
To add the medibuntu repos, follow this guide

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by AeThEr777 on 2008-04-15
ok Im assuming im only inputing the "Ubuntu 7.10" command into the terminal for installing the Medibuntu repos? I input the command into the terminal and it asked me for a sudo password. whats my password i try to type in the login password but my keybaord wont type into the terminal.

AeThEr777

---

### Post by Inxsible on 2008-04-15
> **AeThEr777 said:**
> ok Im assuming im only inputing the "Ubuntu 7.10" command into the terminal for installing the Medibuntu repos? I input the command into the terminal and it asked me for a sudo password. whats my password i try to type in the login password but my keybaord wont type into the terminal.

AeThEr777Yes only perform the commands for 7.10. and yes its your login password. and dont worry about it not showing any *'s or .'s.

It is taking in your password. Just type it in and hit enter

---

### Post by AeThEr777 on 2008-04-15
Ok I have completed the steps highlighted under the Subtitle "Adding the Repositories" Do i have to do the additional steps or can i stop there?

---

### Post by Inxsible on 2008-04-15
> **AeThEr777 said:**
> Ok I have completed the steps highlighted under the Subtitle "Adding the Repositories" Do i have to do the additional steps or can i stop there?
Now you open up a terminal and type in```
sudo aptitude safe-upgrade && sudo aptitude install amarok
``` You added the medibuntu repos correct?

---

### Post by AeThEr777 on 2008-04-15
Yup I did! Can I go ahead with ur next step?

---

### Post by rocknrolf77 on 2008-04-15
> **Frenske said:**
> I use songbird on Linux, because I did not like the ubuntu default player (whatever that was) but it is not even near iTunes. It is slow to start up and not really responsive; it might be the just the Linux version and I suspect that the Mac is what the developers are mainly using. It plays the songs and it looks good and it feels a bit like iTunes.

Perhaps I make it sound it is a bad program. Considering it is still more or less in the beta phase (version 0.5 was just brought out) it is a capable program. It might be an ugly duckling now but giving the time it might grow in a beautiful swan. ;)

What are you talking about.... Rhythmbox is the most responsive player I have ever used. It's like itunes but without the bloat. KISS (keep it simple stupid)

---

### Post by mister_pink on 2008-04-15
Can I recommend "listen". It's not a widely used player but I absolutely love it for its features like looking up artists and albums in wikipedia and finding lyrics. Its got oodles of potential for those of us that like simple players. Its layout and behaviour is mostly a lot like rhythmbox.

---

### Post by Inxsible on 2008-04-15
> **AeThEr777 said:**
> Yup I did! Can I go ahead with ur next step?Yes. just use the two commands to install Amarok. You should now have Amarok under Applications>>Sound and Video>>Amarok

---

### Post by Inxsible on 2008-04-15
> **mister_pink said:**
> Can I recommend "listen". It's not a widely used player but I absolutely love it for its features like looking up artists and albums in wikipedia and finding lyrics. Its got oodles of potential for those of us that like simple players. Its layout and behaviour is mostly a lot like rhythmbox.
I think Rhythmbox and Amarok also look up artists and albums from Amazon's web service i think

---

### Post by AeThEr777 on 2008-04-15
This is totally off topic but i put the command in the terminal and i minimized the terminal and now i cant find the terminal it isnt in the taskbar anemore like before compiz was enabled so i cant find it. If you can tell me where i can find that window i can paste the prompt that i was talking about

AeThEr777

---

### Post by Inxsible on 2008-04-15
> **AeThEr777 said:**
> This is totally off topic but i put the command in the terminal and i minimized the terminal and now i cant find the terminal it isnt in the taskbar anemore like before compiz was enabled so i cant find it. If you can tell me where i can find that window i can paste the prompt that i was talking about

AeThEr777I am confused. what commands are you talking about?

In any case compiz should have nothing to do with your task bar, so I am not sure why you cant see your task bar. Maybe you closed the terminal, just open the terminal again and try out whatever commands you are talking about.

---

### Post by AeThEr777 on 2008-04-15
Nvm I just restarted the comp and the taskbar is back. Ummmm the prompt i get when installing Amarok from the terminal is:

"Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
amarok [Not Installed]
amarok-xine [Not Installed]

Score is -9872

Accept this solution? [Y/n/q/?] "

Yes No or Q?

---

### Post by Inxsible on 2008-04-15
> **AeThEr777 said:**
> Nvm I just restarted the comp and the taskbar is back. Ummmm the prompt i get when installing Amarok from the terminal is:

"Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
amarok [Not Installed]
amarok-xine [Not Installed]

Score is -9872

Accept this solution? [Y/n/q/?] "

Yes No or Q?Say no to it and it will probably offer you another suggestion. or you can simply quit (Q)

and then try this```
sudo aptitude install amarok amarok-xine
```

---

### Post by AeThEr777 on 2008-04-15
Now I got this prompt 

"Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
amarok [Not Installed]
amarok-xine [Not Installed]

Score is -19812

Accept this solution? [Y/n/q/?] "

Yes No or q?

---

### Post by AeThEr777 on 2008-04-15
My score is a lot worse for that one lol

---

### Post by AeThEr777 on 2008-04-15
what do i say for this prompt?

---

### Post by Inxsible on 2008-04-15
> **AeThEr777 said:**
> what do i say for this prompt?just quit using Q.

then use the ```
sudo aptitude install amarok amarok-xine
``` and say yes for the 1st option

---

### Post by AeThEr777 on 2008-04-15
UH oh first option? I just said yes for the second prompt as well! I thought you meant say yes for that entire cmd. Is that bad

AeThEr777

---

### Post by Inxsible on 2008-04-15
> **AeThEr777 said:**
> UH oh first option? I just said yes for the second prompt as well! I thought you meant say yes for that entire cmd. Is that bad

AeThEr777Just check if it installed Amarok on your rig. Applications>>Sound & Video>>Amarok

---

### Post by AeThEr777 on 2008-04-15
Nothing showed up! Still the original programs

---

### Post by Inxsible on 2008-04-15
Open up Synaptic Package Manager by going to System>>Administration>>Synaptic Package Manager. Search for "amarok" without quotes and then right click on it and select Mark for Installation.

---

### Post by AeThEr777 on 2008-04-15
I marked it for install and got the following error msg:

"Could not mark all pakages for installation or upgrade
 - the following pakages have unresolved dependencies make sure all repositories are added and enabled in the preferences"

Im pretty sure i added all those repose that u mentioned. I followed ur terminal cmds. Did i miss one?

---

### Post by oldos2er on 2008-04-15
"Did i miss one?"

 Try this in a terminal: sudo aptitude update && sudo aptitude install amarok

---

### Post by wyth on 2008-04-16
> **Frenske said:**
> I use songbird on Linux, because I did not like the ubuntu default player (whatever that was) but it is not even near iTunes. It is slow to start up and not really responsive; it might be the just the Linux version and I suspect that the Mac is what the developers are mainly using. It plays the songs and it looks good and it feels a bit like iTunes.

Perhaps I make it sound it is a bad program. Considering it is still more or less in the beta phase (version 0.5 was just brought out) it is a capable program. It might be an ugly duckling now but giving the time it might grow in a beautiful swan. ;)


> **rocknrolf77 said:**
> What are you talking about.... Rhythmbox is the most responsive player I have ever used. It's like itunes but without the bloat. KISS (keep it simple stupid)

Frenske's calling Songbird slow and unresponsive, not Rhythmbox.  Note version 0.5; Rhythmbox is at 0.11.5.

Keep it simple stupid?  A good place to start is by reading what's actually written.

---

### Post by rye79 on 2008-04-17
I purchase songs from amazon.com mp3 downloads and play them songs in Amarok.  It's a good combination.  Banshee is also a good player, but I prefer Amarok.

I used to miss itunes solely because I liked to purchase individual songs and I knew it was 100% legal.  Now amazon.com supports Ubuntu and downloading their proprietary software is optional.  I can once again buy songs for $0.89 to $0.99 per track and use Amarok.  I am so happy!  

Hope this helps.

---

