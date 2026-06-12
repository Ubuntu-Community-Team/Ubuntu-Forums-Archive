---
title: "GAIM vs Pidgin"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by milkolate on 2007-07-02
Which is better?
I want to try Pidgin but I can't find it in the Add/REmove Applications..
My problem with GAIM is that it doesn't copy the Contact Details from my YM!

---

### Post by Kosimo on 2007-07-02
> **milkolate said:**
> Which is better?
I want to try Pidgin but I can't find it in the Add/REmove Applications..
My problem with GAIM is that it doesn't copy the Contact Details from my YM!

Pidgin 2.02 has hundreds of bugfixes from the latest gaim 2.0 beta. I really recommend you to upgrade.

You can download pidgin form the website and compile it...
Or if you really want an easy way to install it, just go here

[GetDeb Pidgin 2.0.2]("http://www.getdeb.net/release.php?id=1045")

Download this two debs from that site and install it.
First pidgin-data and then pidgin.
After this, you'll see the new entry in internet menu.

(Is not necessary but i recommend to uninstall gaim before installing pidgin)

Cheers

---

### Post by milkolate on 2007-07-02
how do i uninstall gaim? Add/REmove Applications cannot remove it

---

### Post by meborc on 2007-07-02
you can uninstall it by doing ```
sudo apt-get remove gaim
```
but this will also uninstall the ubuntu-desktop metapackage as it depends on gaim

there is no problem with just leaving the gaim as it is... no need to uninstall it

---

### Post by Kosimo on 2007-07-02
> **milkolate said:**
> how do i uninstall gaim? Add/REmove Applications cannot remove it

As I said...
Is not necessary...

But If you want to uninstall it.
go to Synaptic and search gaim. Then choose completely remove. and Apply

Done.

---

### Post by nitro_n2o on 2007-07-02
> **milkolate said:**
> how do i uninstall gaim? Add/REmove Applications cannot remove it

open  your terminal and type this: 

```
sudo apt-get remove gaim
```

---

### Post by moredhel on 2007-07-02
Yeh, it wouldn't uninstall for me either, just leave it and install pidgin. alternatively, you could try and find someone's personal repository that will actually upgrade your pc from gaim to pidgin properly.

I can give you a good one when I get home :)

---

### Post by Kosimo on 2007-07-02
> **meborc said:**
> you can uninstall it by doing ```
sudo apt-get remove gaim
```
but this will also uninstall the ubuntu-desktop metapackage as it depends on gaim

there is no problem with just leaving the gaim as it is... no need to uninstall it

True...
Anyway, when installing that debs it install all dependencies that pidgin needs.

;)

---

### Post by milkolate on 2007-07-02
**HELP!**
The Getdeb Pidgin site doesn't work.
I can't understand the instructions in the Pdgin site. Heeeeelp!

---

### Post by meborc on 2007-07-02
the site seems to be down at the moment...

if you get to getdeb.net then download the deb files of pidgin 2.0.2 to your desktop

then install them```
sudo dpkg -i /home/<USERNAME>/Desktop/pidgin*
```
where the <USERNAME> is your user name :D

---

### Post by Dark Star on 2007-07-02
Pdigin ftw.. Btw to uninstall Gaim.. U can u se those meathods stated above or.. Open Synaptic Manage .. In the Search type Gaim.. Now after Search will end Click on the box with Green Colour .. Hollow boxes states Not Installed aaps.. Now Right Clikc on Gamin Green Box and select **Mark for Complete Removal** clikc Apply and u are done.. hope this helps...

Peas Ds

---

### Post by Kosimo on 2007-07-02
> **milkolate said:**
> **HELP!**
The Getdeb Pidgin site doesn't work.
I can't understand the instructions in the Pdgin site. Heeeeelp!

lol..

Was working just some minutes ago... Maybe they're updating something..
Try again in a few minutes...

---

### Post by milkolate on 2007-07-02
Thanks for the info.. I've chosen not to uninstall GAIM...
The GetDeb site is down.
How do I install from the Pidgin official site?

---

### Post by Dark Star on 2007-07-02
[http://www.kalpiknigam.com/blog/2007/05/12/install-pidgin-200-on-ubuntu-feisty-with-all-plugins/](http://www.kalpiknigam.com/blog/2007/05/12/install-pidgin-200-on-ubuntu-feisty-with-all-plugins/)

Get the .deb file from here .. Hope it helps.. I downloaded from here and it works fine here :D

---

### Post by Kosimo on 2007-07-02
> **Dark Star said:**
> [http://www.kalpiknigam.com/blog/2007/05/12/install-pidgin-200-on-ubuntu-feisty-with-all-plugins/](http://www.kalpiknigam.com/blog/2007/05/12/install-pidgin-200-on-ubuntu-feisty-with-all-plugins/)

Get the .deb file from here .. Hope it helps.. I downloaded from here and it works fine here :D

This one looks the 2.0.0 version...

Better if installs the latest 2.0.2...

---

### Post by milkolate on 2007-07-02
i already got the 2 .deb files from getdeb.. how do i install it? do i install both?

---

### Post by Dark Star on 2007-07-02
> **milkolate said:**
> i already got the 2 .deb files from getdeb.. how do i install it? do i install both?
To install just open the .deb pack by double clicking it and it will get installed auto matically ;)

---

### Post by black_ice on 2007-07-02
as u saw ..... just but this command before the name of the package.deb 

dpkg -i  <the name of the package.deb> 

and it will start the installation process

---

### Post by milkolate on 2007-07-02
Which package do i install first?

---

### Post by milkolate on 2007-07-02
ah i got it, I first need to install the dependency.. I will be installing it after my other installations.

---

### Post by Kosimo on 2007-07-02
> **milkolate said:**
> ah i got it, I first need to install the dependency.. I will be installing it after my other installations.

Success?

;)

---

### Post by milkolate on 2007-07-02
Yup, I was successful, but I am faced with the same problem as in GAIM. The Contact details of my Yahoo messenger contacts are not carried over in Pidgin. Therefore, I don't know who my buddies are. I have to manually create an Alias for each.

---

### Post by Raineer on 2007-07-02
Wow, that is very strange....Mine works fine in Pidgin.

---

### Post by Dark Star on 2007-07-02
> **milkolate said:**
> Yup, I was successful, but I am faced with the same problem as in GAIM. The Contact details of my Yahoo messenger contacts are not carried over in Pidgin. Therefore, I don't know who my buddies are. I have to manually create an Alias for each.
Same here. U must be using Hotmail.. isn't it ? Thats why I created a yahoo account for Yahoo Frnds :)

---

### Post by milkolate on 2007-07-02
I'm using Yahoo

---

### Post by GoneWithTheWind on 2007-07-02
Hi,

I'm using 6.06 and have used Gaim for a year.  It has worked fine - until today I clicked some annoying update that kept coming up for Gaim and now it keeps starting to load, gets 1/2 way and then stops.

What do I need to do to get it working again?

I went to the Pidgeon side and some of the comments said 2.02 is unstable.  Also, the download is for Feisty.  

:(

What should I do?

---

### Post by GoneWithTheWind on 2007-07-02
This is funny.

I started gyachi and used it for a bit, then tried gaim again.

It started and kicked off gyachi.

A little competition can help things along.  :)

---

### Post by GoneWithTheWind on 2007-07-14
I'm using gaim 1.5.1, which works well but doesn't have sound in the rooms and no webcam.

What can I do to upgrade for having these?

Thanks.  :)

---

### Post by mike102282 on 2007-07-14
> **milkolate said:**
> Which is better?
I want to try Pidgin but I can't find it in the Add/REmove Applications..
My problem with GAIM is that it doesn't copy the Contact Details from my YM!


Pidgin is Gaims new name!

---

### Post by GoneWithTheWind on 2007-07-15
> **John Rupp said:**
> I'm using gaim 1.5.1, which works well but doesn't have sound in the rooms and no webcam.

What can I do to upgrade for having these?

Thanks.  :)

Still looking for an answer for this.

Thanks.

---

### Post by CityofAsh on 2007-07-19
I compiled the latest version of pidgin from source. Only problem with it i found is i cannot transfer files to AIM users. So i just kept gaim installed in case the need to transfer. 

I like the pidgin interface better then gaim. Basically it is the same just has support of rmore IM/Chat Clients. Anyone know of addons or plugins to enable yahoo voice in pidgin? I tried gyachi and it does not let my mic work. 

~City

---

### Post by CityofAsh on 2007-07-19
> **John Rupp said:**
> Hi,

I'm using 6.06 and have used Gaim for a year.  It has worked fine - until today I clicked some annoying update that kept coming up for Gaim and now it keeps starting to load, gets 1/2 way and then stops.

What do I need to do to get it working again?

I went to the Pidgeon side and some of the comments said 2.02 is unstable.  Also, the download is for Feisty.  

:(

What should I do?

Compile it from source it worked for me.

---

### Post by Kosimo on 2007-07-19
> **CityofAsh said:**
> I compiled the latest version of pidgin from source. Only problem with it i found is i cannot transfer files to AIM users. So i just kept gaim installed in case the need to transfer. 

I like the pidgin interface better then gaim. Basically it is the same just has support of rmore IM/Chat Clients. Anyone know of addons or plugins to enable yahoo voice in pidgin? I tried gyachi and it does not let my mic work. 

~City

I recommend you to wait... In a few days Pidgin 2.0.3 will be released. (Is already a week late, have a look to pidgin [roadmap]("http://developer.pidgin.im/roadmap")) You can check the closed tickets for this released, you may find this bug.
;)

---

### Post by loell on 2007-07-19
> **CityofAsh said:**
> I compiled the latest version of pidgin from source. Only problem with it i found is i cannot transfer files to AIM users. So i just kept gaim installed in case the need to transfer. 

I like the pidgin interface better then gaim. Basically it is the same just has support of rmore IM/Chat Clients. Anyone know of addons or plugins to enable yahoo voice in pidgin? I tried gyachi and it does not let my mic work. 

~City

why not just use gizmo 3.x for the voice part, it will require you to make several steps to call yahoo messenger, but it does work.

---

### Post by misfitpierce on 2007-07-19
I like GAIM better than pidgin for the Festival talking plugin... not sure if its avail for pidgin.

---

### Post by GoneWithTheWind on 2007-08-07
> **CityofAsh said:**
> Compile it from source it worked for me.

Thanks.

I would, if I knew how to do that.  #-o

---

### Post by Lutherian on 2008-03-22
For what it's worth ...

I understand that they had to change their name from GAIM to something else because of greedy suites who didn't like the similarity to AIM, but really!! did they HAVE to call it Pigeon!! and purple agh no man!
I mean was there a flash back to 1983 - was someone listening Prince or O+(->
I've looked at the specs - I *really* don't see any difference between Pigeon and Gaim - none!

Ok, so here's the deal:

If you want the webcam, voice chat stuff - forget gaim / pidgeon there other solutions.

I'm sticking with Gaim 'cuase (1) it looks soo much better (2) I can tweak it in simple ways: it's simple and clean interface - looks almost like it belongs in Ubuntu - if the just shifted the yellow to orange - it would've been perfect. (^_^)

---

