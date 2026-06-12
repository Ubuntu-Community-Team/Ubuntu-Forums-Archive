---
title: "[SOLVED] problems with synaptic package manager &amp;amp; update manager &amp;amp; editing sources.li"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by mrdes on 2007-10-16
hi ...
simply when i try to access any of these i got these errors :
1- synaptic package manager
error=
[COLOR="Red"]E: Malformed line 4 in source list /etc/apt/sources.list (URI)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
[/COLOR]

2- update manager
error=
[COLOR="Red"]Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 4 in source list /etc/apt/sources.list (URI), E:The list of sources could not be read.[/COLOR]

3- editing sources.list :
error=
[COLOR="Red"]Could not open the file /etc/apt/sources.list.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.[/COLOR]


so , would some one help me with that ?:confused:
thanks
SEE ATTACHMENTS

---

### Post by overdrank on 2007-10-16
Hi did you use this command to edit your apt list
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by qpieus on 2007-10-16
Hmmm, sounds like your sources.list file got corrupted somwhow. Try using cat to look inside that file```
cat /etc/apt/sources.list
```
If successful you'll see the text from the file scroll by in your terminal. If that worked then,back in the terminal, type```
cat /etc/apt/sources.list > tempfile
```
This will output the contents to a new text file called tempfile. Post the contents of this new file here and maybe we can figure out what the problem is.

---

### Post by mrdes on 2007-10-16
i did.
it returnes the same problem as i said :
[COLOR="Red"]
Could not open the file /etc/apt/sources.list.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.[/COLOR]

---

### Post by mrdes on 2007-10-16
> **qpieus said:**
> Hmmm, sounds like your sources.list file got corrupted somwhow. Try using cat to look inside that file```
cat /etc/apt/sources.list
```
If successful you'll see the text from the file scroll by in your terminal. If that worked then,back in the terminal, type```
cat /etc/apt/sources.list > tempfile
```
This will output the contents to a new text file called tempfile. Post the contents of this new file here and maybe we can figure out what the problem is.

i couldn't find the tempfile. !

---

### Post by qpieus on 2007-10-16
The tempfile should be in your home directory (or whatever directory your terminal window was open in, if it was not home).

Was cat able to display the sources.list file contents?

---

### Post by mrdes on 2007-10-16
the tempfile says :
[COLOR="DimGray"]
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[]/ feisty main
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security restricted main multiverse universe #Added by software-properties

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable
deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main
[/COLOR]


> **qpieus said:**
> Was cat able to display the sources.list file contents?

yes it displayed the sources.list content 

and thank u for fast reply

---

### Post by qpieus on 2007-10-16
It looks like line 4 is this:```
deb cdrom:[]/ feisty main
```

The [] in the line must be messing up synaptic. 

Open up your tempfile in gedit and put a # sign in front of that line 4, like this:```
#deb cdrom:[]/ feisty main
```
This line is referring to your ubuntu cd, which you really don't need any more to since you can update from the ubuntu repos. The # sign makes the pc ignore this line.

Next, make a backup copy of the original sources.list file:```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_bu 
```

Now delete the bad sources.list:```
sudo rm /etc/apt/sources.list
```
Then move your tempfile into the /etc/apt directory and rename it as sources.list:```
sudo mv tempfile /etc/apt/sources.list
```

Now load synaptic again. If we cleared the problem synaptic should load properly.

---

### Post by mrdes on 2007-10-16
> Open up your tempfile in gedit and put a # sign in front of that line 4

it can't be opened , says:
[COLOR="Red"]Could not open the file /home/mr-des/tempfile.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.[/COLOR]
which is the the same error when i try to edit sources.list

---

### Post by mrdes on 2007-10-16
[COLOR="Blue"][B]The problem solved .

thanks alot.
[/B][/COLOR]

---

### Post by iansane on 2007-10-16
Just wanted to comment. It is useful to use # to comment out lines. You can comment and uncoment lines anytime and then do apt-get update in terminal. I have been having trouble with a couple of updates because fiesty and gutsy are both in my sourses.list since I upgraded. You might have trouble from upgradeing at some point in time and need to comment out lines, but then some howto's will tell you to use the fiesty, dapper, or edgy repos to install a particular package. It can become a little experimental at that point. I have found it better to use terminal for any synaptic related tasks (apt-get). and only use synaptic to see if a package is available and what the correct name of it is. I guess that's preference though. I really don't like terminal but I seem to have better luck since I learned a few commands.

---

### Post by qpieus on 2007-10-16
> **mrdes said:**
> [COLOR="Blue"][B]The problem solved .

thanks alot.
[/B][/COLOR]

Good job. What's with gedit not opening that file? How did you ultimately solve the problem?

---

### Post by mrdes on 2007-10-16
I don't how did i solve it . I just followed your steps and skip the first one ..
actually the synaptic package showed the installed packages only.

---

### Post by mrdes on 2007-10-16
how can i add more packages to the synaptic.
and what is "third party" 
sorry if i'm bothering you with my questions .

---

### Post by overdrank on 2007-10-17
> **mrdes said:**
> how can i add more packages to the synaptic.
and what is "third party" 
sorry if i'm bothering you with my questions .

Hi I glad you solved your issue and this link may help when adding repo's
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
Good luck!
Edit if you could mark this thread as solved thanks

---

### Post by qpieus on 2007-10-17
No bother. Follow overdrank's link for a nice info page on repositories. A *third party* repository is a repo that is not maintained by ubuntu (Canonical), they are maintained by other companies or even individuals. There are lots of third party repos - for the wine program, automatix, compiz, etc.

So to answer your question, you "add" more program (choices) in synaptic by enabling all of the available ubuntu repos (main, restricted, universe, multiverse) and by adding any third party repos you want. Then synaptic will examine all of your repos and list the available packages. Note: after you enable new repos in synaptic you need to click on "reload" so synaptic can generate a new package list.

---

### Post by mrdes on 2007-10-17
[B]Thank you all ..
that was really helpful ..[/B]

---

