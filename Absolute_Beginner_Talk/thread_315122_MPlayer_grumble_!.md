---
title: "MPlayer grumble !"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by Radiolad on 2006-12-08
OK. So I'm really liking Dapper BUT ... why Oh why is all this program downloading  (using Synaptic ) frought with problems. Mr Gates will continue to rake in the dollars as long as there are numerous DISADVANTAGES to using Ubuntu software ](*,) You only have to view the  endless list of cries for assistance (including my own!) to see this. 
I have installed MPlayer and can see the GUI, but if I try to view a video from the BBC, the message on screen shows 'buffering' taking place followed by info ***NOT*** video of what I _should_ be seeing :evil: 
When I stop the Mplayer (which is not showing anything useful) I get booted off the browser completly; how frustrating is that  ](*,) 

Can anyone ***_please_*** help this newbie??
Cheers,  Radiolad

---

### Post by tommytom on 2006-12-08
Are you using MPlayer or MPlayer-plugin through firefox? If it's the stand alone player try using firefox Mplayer plugin which you can get from Synaptic if the opposite is true attempt to paste the URL in to the stand alone player. Sorry i'm in a rush so i can't stay to help :( gotta catch me buddies it's FRIDAY :) Good Luck! i will call in on this thread tomorrow so keep us posted, but i'm sure someone much more l33t than me will be able to help you.

---

### Post by breid on 2006-12-08
You need RealPlayer to view video from BBC, this can be dowloaded using Synaptic. To stop flickering whilst viewing video go to Applications > Sound & Video > RealPlayer10 click on "Hardware" and disable "Use XVideo". Hope this helps.

---

### Post by Radiolad on 2006-12-09
> **breid said:**
> You need RealPlayer to view video from BBC, this can be dowloaded using Synaptic. To stop flickering whilst viewing video go to Applications > Sound & Video > RealPlayer10 click on "Hardware" and disable "Use XVideo". Hope this helps.

Hi folks!
Try as I might I cannot get MPLAYER in any of its forms to run. I have also downloaded Realplayer from the RP website.
It shows to be executable, but does not/ will not install.
**I am using an iMac** .... does this make a difference?
  *The cat is now sitting on my lap so I'm having to type with one hand ](*,) ](*,) :rolleyes: *

NEWBIE IN A QUANDRIE ........ Radiolad

---

### Post by tommytom on 2006-12-09
Hey Radiolad,
  i don't think that the fact you are using a imac should make any difference what i will suggest ( i sound like a broken record on this one:)) is that you follow the link in my signiture and use Automatix to install realplayer i would have said last night but i was in a rush and forgot to mention it. Arrgh!! fluffy animals near computers, i feel faint!! i put enough hair into my machine with out anybodys help;)
Any way keep us posted!

---

### Post by Radiolad on 2006-12-09
Hi Tommytom,  Well...[COLOR="Red"]Red [/COLOR]on Black! (my eyes!) I will give your advice a try. It will have to be the PPC version due to the iMac from what I can make out.  All this 'text' stuff frightens the life out of me; give me an old **valve **radio any day!!!!
Cheers for now .... I will be back!      RADIOLAD

---

### Post by Radiolad on 2006-12-09
> **Radiolad said:**
> Hi Tommytom,  Well...[COLOR="Red"]Red [/COLOR]on Black! (my eyes!) I will give your advice a try. It will have to be the PPC version due to the iMac from what I can make out.  All this 'text' stuff frightens the life out of me; give me an old **valve **radio any day!!!!
Cheers for now .... I will be back!      RADIOLAD

Hi Tommytom. OK I'm a failure.:(  Would you be kind and ***NEWBIE-Fi*** the instuctions... as they sure don't want to work for me and my little old iMac


 [COLOR="SeaGreen"]Installing on (K,X)Ubuntu 6.06 PowerPC (Dapper)

Edit your sources.list:

sudo gedit /etc/apt/sources.list

Substitute gedit with the text editor of your choice. [COLOR="Black"](WHAT IS THIS??)[/COLOR]

Add the following to your sources.list:

NOTE: Xubuntu users will need to uncomment all the additional sources as well as add the automatix repository.

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

Next you must get our GPG key in order to authenticate our repository:

wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -

To finish off:

sudo apt-get update
sudo apt-get install automatix

Xubuntu users will also need to install Zenity:

sudo apt-get install zenity

Run Automatix either with the command "automatix" or by its launcher in Applications>System Tools>Automatix.[/COLOR] [COLOR="Black"] (WHERE IS THIS??)[/COLOR]

 :rolleyes: RADIOLAD:rolleyes:  N.B wording in BOLD is mine:???:

---

### Post by tommytom on 2006-12-09
Hey Radiolad!
           Ok lets do this step by step. First do you know how to use a terminal? You can find the terminal in the menu bar look for Applications (top left of the screen) then Accessories then Terminal (also expressed as Applications>Accessories>Terminal) you have seen this on the Automatix web page > Applications>System Tools>Automatix Now you should have a terminal open it will display something like this ```
tom@the-alamo:~$
``` Now you can enter the comands from the web page```
sudo gedit /etc/apt/sources.list
``` simply copy this from the site and paste into the terminal. It should prompt you for your password.

---

### Post by Radiolad on 2006-12-09
Hi Tommytom
I'm now down to this line;
Run Automatix either with the command "automatix" or by its launcher in Applications>System Tools>Automatix.
    But where is this??

---

### Post by tommytom on 2006-12-09
Ok your almost there now! Using your terminal type
 ```
sudo automatix
```

EDIT  Did you save the file sources.list after editing it in gedit?

---

### Post by Radiolad on 2006-12-09
> **tommytom said:**
> Ok your almost there now! Using your terminal type
 ```
sudo automatix
```

EDIT  Did you save the file sources.list after editing it in gedit?

Hi Tommytom
I've had to swap onto my 'windows' PC as my iMac has done his trick of switching off after approx 90 mins :evil: 

Regarding the :-   sudo automatix line,  I have been putting this in like this  sudo "automatix"
Should it just be   sudo automatix
And what do you mean about EDIT ... Did you save etc ....??
RADIOLAD:(

---

### Post by tommytom on 2006-12-09
Ok Radiolad don't put quotation marks into commands.
When you enter ```
sudo gedit /etc/apt/sources.list
```
a text editor should have opened (it looks like notepad in windows) you should have added this line to it ```
deb http://www.getautomatix.com/apt dapper main
``` and then saved the document. Then entered this into the terminal ```
wget http://www.getautomatix.com/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
```
Next enter this into the terminal ```
sudo apt-get update
```
then```
sudo apt-get install automatix
```
then run Automatix ```
sudo automatix
```
Ok just follow that you need to be coneccted to the web the whole time.
Right got a film to make so I'm off.Keep at it;)

---

### Post by Radiolad on 2006-12-09
Thanks Tommytom,
I'll try all this out tomorrow when iMac has cooled down and get back to you.
What film are you making????
Cheers   Radiolad

---

### Post by tommytom on 2006-12-09
> Right got a film to make so I'm off Oops typo making me sound more intreasting than i'm:oops: i went to see a 3D film Creature From The Black Lagoon it was hilariously 1950's

---

### Post by Radiolad on 2006-12-10
Hi Tommytom.
OK. I've run Automatics, BUT which of the many progs do I choose??
There are approx 4 'Media' type items which I have downloaded and installed ...BUT... I still can't run the BBC player....so I'm obviously STILL doing something wrong!
Can you advise please?     Many thanks for your time and help todate.
Cheers,   RADIOLAD

---

### Post by tommytom on 2006-12-10
Did you install Realplayer? If you did then open it and got to  file>open location  simply cut and paste the URL of the stream you wish to watch into the prompt. We will get there eventually don't you worry this is all part of the FUN:rolleyes:

---

### Post by Radiolad on 2006-12-10
> **tommytom said:**
> Did you install Realplayer? If you did then open it and got to  file>open location  simply cut and paste the URL of the stream you wish to watch into the prompt. We will get there eventually don't you worry this is all part of the FUN:rolleyes:

Hi Tommytom,
I **cannot ***SEE *Realplayer in the progs within Automatics, however I can *SEE *it in the CANONICAL list which I managed to suck into my available list of progs, unfortunately I go round in circles with the 'acceptance button' / updating /acceptance button ](*,) ](*,) .....oh my :-? 
Pleeeeeeese advise!
(One good thing...I've attached an old PC fan to the top of the iMac with the aid of a tupperware lid and doublesided sticky pads and guess what ...yes you guessed it....it's *STILL *on 3.5 hours later and still going :-D .    Don't ya just luv glue and string!)
    Hoping for more advice, regards  RADIOLAD

---

### Post by tommytom on 2006-12-10
Very ingenious Radiolad well done mate thats real hacking! Ok I think i need to apologise to you as I got you to install automatix and it should have been  automatix2 which has a GUI to rectify this problem follow these steps. Just cut and paste the following commands.
```
sudo apt-get remove automatix 
```
>   Installing on (K,X)Ubuntu 6.06 i386,amd64 (Dapper)

From terminal do the following (ONE LINE AT A TIME HITTING ENTER AFTER EACH STEP):

```
 echo "deb http://www.getautomatix.com/apt dapper main" | sudo tee -a /etc/apt/sources.list
 wget http://www.getautomatix.com/apt/key.gpg.asc
 gpg --import key.gpg.asc
 gpg --export --armor 521A9C7C | sudo apt-key add -
```

Then 
```
sudo apt-get update
```
followed by
```
sudo apt-get install automatix2
```
 
 That will get you the updated version which should make things easier it also gives you the option to add other programs and w32codecs for playing wmv files

---

### Post by Radiolad on 2006-12-10
Hi Tommytom,
Before I go ahead with the download, I am running a PPC (iMac) which is not covered: [COLOR="Magenta"]Installing on (K,X)Ubuntu 6.06 i386,amd64 (Dapper)[/COLOR] Unless you feel it will run ??
Can you advise.     
(N.B. iMac *still *running for 6 hours with tupperware/fan mod!)
     EEE YUV GOT T LAFF  !!     Radiolad

---

### Post by tommytom on 2006-12-11
> **Radiolad said:**
> Hi Tommytom,
Before I go ahead with the download, I am running a PPC (iMac) which is not covered No you are right about that, sorry i forgot that Mac only started using Intel recently :-k. I was sure that Realplayer was one of the applications you could install using automatix but it ain't. I have to say that trying to help you has just proved to me how much i still have to learn!! So if you can deal with another change of direction lets try to install the linux (.bin) version of Realplayer you downloaded earlier.

 First open a terminal
 next go to the directory where Realplayer was downloaded to using the command "cd" (change directory)
```
Radiolad@hiscomputer:~$cd /home/radiolad/downloads
```
Change the directory names as needed and use the tab button to finish directory and file names, double tap it if there are multiple files with similar names to view them, if you want to look into a directory to find a file with out actually changing directory use the command "ls" 
```
Radiolad@hiscomputer:~$ls /home/radiolad/downloads
```

Ok we are now in the directory /downloads where you downloaded real player (wherever that is on your machine) and your terminal will display something like this.

```
Radiolad@hiscomputer:~/home/radiolad/downloads$
```

now "ls" this directory like so
```
Radiolad@hiscomputer:~/home/radiolad/downloads$ls
```

Your terminal displays this
```
Radiolad@hiscomputer:~/home/radiolad/downloads$ls
RealPlayer10GOLD.bin
```

Follow these instructions from the web site-

> Installation Instructions

- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player.

- Enjoy your RealPlayer10 for Linux! 
 The parts within the quotation marks are commands simply copy them into the terminal, making sure you are still in the correct directory, and without the quotation marks if this still dosn't work attempt to "sudo" the commands 
[code]sudo chmod a+x RealPlayer10GOLD.bin[/quote] for example and so on. And finally after days of me taking you down dead ends and totally undermining my own confidence you should finally have Realplayer and BBC Clips [-o<

 Ps well done with the Mac hack, i wish i could see it must look really quite strange a modern computer kept running by tupperware! Can you imagine what's holding the International Space Station together? probably chewing gum and potatoes LOL

EDIT- **OMG it's just got more difficult Realplayer 10 dosn't support PPC chips you need Realplayer8 follow this link [http://forms.real.com/real/player/blackjack.html?platform2=Unix&product=RealPlayer%208&proc=Linux/PPC&lang=en&show_list=0](http://forms.real.com/real/player/blackjack.html?platform2=Unix&product=RealPlayer%208&proc=Linux/PPC&lang=en&show_list=0)**
follow the same instructions substituting Realplayer 8 for RealPlayer 10.

---

### Post by Radiolad on 2006-12-12
Thanks Tommytom for the additional info. I'll give it a try when my other-half has finished with the WEB (Next stop....a ROUTER !)
Re iMac...I noticed on a site showing how to 'undo' the case of the earlier G3 models that it DID have a built in fan! Interesting that the 'MAC Bods' decided to do without one in suceeding models!
The casing on mine (with tupperware mod) actually feels cold to the touch even after 6 hours as opposed to 'rather warm' without it fitted !!!!!
You can tell I was a BLUE PETER baby! (washing-up bottles and sticky-back plastic... and of course an OBLONG (not a rectangle)
    Cheers,  RADIOLAD  (I'll let you know how I get on)

---

### Post by tommytom on 2006-12-12
Hey Radiolad I posted a link to this thread in the Apple PPC Users forum and recieved a reply from ssam
 > There is a realplayer 10 for powerpc, its just very hard to find

[https://player.helixcommunity.org/2005/downloads/](https://player.helixcommunity.org/2005/downloads/)
its in the Archived Releases section, and is an old version

i think it installs in a similar way to the x86 installer version.

i think libstdc++5 might need to be installed to make it work (but i am not 100% sure) - ssam 

Heres the link to that post [http://www.ubuntuforums.org/showthread.php?t=317042](http://www.ubuntuforums.org/showthread.php?t=317042)

Just let me know if you are still unsure of what to do (like i will know!)

---

### Post by ]Nbx*cmD[ on 2006-12-12
> Mr Gates will continue to rake in the dollars as long as there are numerous DISADVANTAGES to using Ubuntu software  You only have to view the endless list of cries for assistance (including my own!) to see this. 

You won't see any endless list of cries for assistance in any Micro$oft forum... because they simply don't exist. Free software will ALWAYS have this advantage, everybody helps everybody on real-time. 

You can't criticize it since this is not an enterprise, nobody assures you this is gonna work perfectly in your PC, you don't pay for it and there is no warranty.

Oh, if you want to have it working perfectly and get all your problems solved without having to worry you can contact Canonical (or other GNU/Linux-oriented enterprises) and they'll fix your issues for a reasonable price :)

This is a constructive comment, don't think i'm rude ^_^

---

### Post by Radiolad on 2006-12-13
Hi,
Thanyou for all your help. This is the latest position:-
I have downloaded RP10 for PPC from the link given.  Using a terminal I modified the instructions in order to run:
realplay-10.0.0.297-linux-2.2-libc6-gcc32-powerpc.bin
using the commands
    "chmod atx"
     and then "./"

All this worked perfectly and RP10 was unloaded succesfully.
HOWEVER... I have had to DELETE Mplayer as it insisted on launching itself when attempting to watch a BBC video, and I still cannot get RP10 to launch.
 According to the RP website, the first time I launch RP a screen should appear to guide me though configuration...no such screen appears.

Can anyone shed light on this problem. I feel I'm ALMOST there!
Cheers Radiolad

---

### Post by tommytom on 2006-12-13
[http://www.bbc.co.uk/radio/audiohelp_nix.shtml](http://www.bbc.co.uk/radio/audiohelp_nix.shtml)

This is a link you might find useful later on.
 Other than that I'm totally stumped now, Good luck Radiolad!!  See you around!

---

### Post by Radiolad on 2006-12-13
Thanks Tommytom for your advice and time. I think I've a bit more learnin' to be a-doing on this 'ere 'player' malarky!!!
All good wishes,  RADIOLAD (on his COOL imac)

---

### Post by Radiolad on 2006-12-13
> **']Nbx*cmD[ said:**
> 

You can't criticize it since this is not an enterprise, nobody assures you this is gonna work perfectly in your PC, you don't pay for it and there is no warranty.
This is a constructive comment, don't think i'm rude ^_^

Hiya, Thanks for your reply,
In hidesight I do appear to be 'carping' :rolleyes:  however just because something is 'not an enterprise' does not mean it cannot be criticised. Is this not all part of the learning process? Feed back, good or bad, is necessary for improvement in any environment.
Ubuntu *_is_* excellent but it does have its drawbacks; for example I have spent many a (happy ](*,) ) hour trying to get Realplayer to function but alas, so far, to no avail. I am learning a great deal along the way, but in reality I just want it to work!
The popularity of computers in the home is due to the simplicity of plug&play and friendly GUI. Just take it out  the box a switch it on, no fiddling and twiddling with terminals and text. :p  
I admire everyone involved with the development of Linux in all its many forms and I wish I had 0.001% of their ability, but I don't and probably never will have. I just have to hang onto the coatails of ingenuity and enjoy the ride :roll: 

All good wishes.  RADIOLAD

---

