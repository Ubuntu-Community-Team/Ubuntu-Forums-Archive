---
title: "Help with setting up Intel 536 chipset modem"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by Siani on 2006-10-07
Hullo,
I'm a complete Linux newbie, and I'm trying to set up a dial-up connection under Dapper.  

I bought a specifically hardware dependant modem, managed to use [COLOR="Blue"]scanmodem [/COLOR]to find out the chipset (Intel 536) and went to the Linux download page for that chipset.  I found many pre-compiled drivers, but they were for such Linux's as Suse, Red Hat, Mandrake and Red Flag.  BUT, there was an uncompiled driver, which I downloaded, unzipped, and read the readme.txt file.

On finding the response [COLOR="Blue"]bash: make: command not found[/COLOR], I even managed to get that and install it, but now, when I follow the second part of the instructions (the first being [COLOR="Blue"]make clean[/COLOR], the second being [COLOR="Blue"]make 536[/COLOR]), I find I don't have [COLOR="Red"]autoconfig.h[/COLOR], and the instruction returns ***Error 1.  This is what I get.

[FONT="Courier New"]Module precompile check
Current running kernel is: 2.6.15-23-386
/lib/modules... autoconfig.h does not exist
please install kernel source
make: *** [check] Error 1[/FONT]

There's part of me that's hoping someone out there managed to compile a modem driver for this chipset (and Dapper), but failing that, maybe someone could point me where I need to go next.  I don't know how to install kernel source, and I couldn't find autoconfig.h.

All those years of being good with Windows means NOTHING now!

Thanks in advance - Sian

---

### Post by Siani on 2006-10-08
I've just been reading a HOWTO on just this subject, although the chipset is the 537EP.  When I searched yesterday before submitting my question, I'd searched on Modem, but I hadn't made the search quite specific enough, so this fabulous article (HowTo: Intel 537EP Chipset MODEM driver install on Ubuntu Dapper) didn't show up in the mess of answers I did get.

Can anyone set a link to it - I see there have been some views of my question, so pointing those to the article may help.

Sian

---

### Post by Coburn on 2006-10-09
I really appreciate all you are going through.
I installed Breezy back in March, and learning how to set up my modem was a real trial by fire for me.  I also have years of Windows experience, and it did help a little.

I had access to the Internet via a second hard disk with ME installed (dual boot).  My first Ubuntu install disk was downloaded on my neighbor's cable Internet.  To install the modem driver I assume you have some kind of internet.

Worst-case scenario, you will have to put the package files on a CD or (size permitting) floppies and paste them into your home directory somewhere, and install them with dpkg.  I put them on my Windows disk, enabled it in System -> Disks, and copied them over.

There is no Debian driver for the Intel536 modems.  You can use sl-modem-daemon, which may be on your CD (I don't recall) but on my machine it gives a baud rate error and does not work--even the latest version from Dapper.

I have had pretty good luck with the Intel537EP-2.60.80.1_secure driver from Intel.  Their website, as you said, has a list of options.  Try one.

There is also a patch for Debian that I untar (tar xfvz?) in the main directory of the untarred chipset driver.  I'm sorry--you'll have to search for a link to it, or PM me later.  I don't think it works without the patch.

try <sudo tar xfvz ./Intel*.tar.gz>

You must definitely read the Dialup Modem HowTo on this forum.  The instructions for the 536/537 are correct but slightly incomplete.

You will have to download and install:
build-essential
(which includes your linux headers set--the reference files used for installing new programs)
gcc, gcc-base, and cpp 3.4, all as noted in the HowTo

For you personally--since you expressed doubts--I will explain that Linux needs the headers in order to weave new programs into the filesystem.  The gcc set is your C++ compiler that actually converts the driver into binary code.

If you have any questions about which packages are part of the linux-headers set, open Synaptic and search build-essential.  Pretend to install it and write down the packages that will be installed (dependencies).  I am assuming you have no internet and will have to download them later and install manually.

Which is like this:
sudo dpkg --install <package name>.deb
Password:

Once you have your headers installed (.deb packages do not need to be compiled),
and the modem package (hopefully in its own file named "modem" or other convenient name) is untarred, using either the tar command or file browser/right click menu
and the patch is copied to the modem directory and untarred
you can install it, 
which is as simple as:

make clean
make 536
sudo make install

Then--if all goes well, you just have to configure your internet.

I copy the example wvdial.conf that comes with the modem driver to /etc/wvdial.conf. just like Alan Jackson says:

"when you need love, just click on me
I'll be waiting patiently
at www-dot-memory"

I don't copy much with the mouse, actually.  It was hard for me as a Windows user to get used to the command line, but now I enjoy it.  As long as you know what you are doing--and I usually don't--it actually tells you what the computer is doing.

<(sudo) cp ./Intel* ~/modem> 
But be sure when you use * that the name is unique to the file/dir you are copying.

Besides the fact you have to make the driver anyway, if you make a mistake with the command line, it tells you what it thinks went wrong.  Then you can do detective work and try again.  In most cases, as the beautiful (inside) Christian math prof that encouraged me when I first started with Linux says, 

"Go ahead and fool around with it.  You probably won't hurt anything permanently."

back to /etc/wvdial.conf:

text-editing the file, I uncomment
#Carrier Check = no
#Stupid Mode = yes
The rest of it I configure using 
<sudo pppconfig>
which is a graphical (ncurses) menu that takes care of the rest of the options.
The most important being phone number, user ID, and password.
For my phone line, I also use the Italian option in wvdial.conf, which adds X3 to the gobbledygook string the modem takes as orders to dial out.  I think of it as "an offer it can't refuse," because for some reason it doesn't seem to hear the dial tone...

Then I use <gnome-ppp> or <wvdial> to connect.  I don't think either come with the CD, but maybe <pon> does.  <sudo pon> just turns on your dialer and away we go. <sudo poff> turns it off.  <sudo> is a must, except for gnome-ppp, because you have to specially configure your /etc/ppp/chap-secrets to let ordinary users access the internet.  Security.

One problem I have is that using either modem_applet (from right-clicking the top panel --> Add to Panel) or the System --> Admin  --> Networking menu to dial out confuses wvdial and pon.  It makes the modem think it is on already, so it aborts the dial.  I had to go into one of the ppp config files and uncomment
#Nopersist
So if I have trouble with the modem, now I just start wvdial and ^c out of it.  That usually shuts it off (nopersist) so it will restart correctly.
<sudo killall wvdial> is another option.  Or <sudo poff>.
If you need specifics, I'll look it up.  Right now I am waiting for an email and then have to go put a CV joint in a car.  

If I can do that, you can do this.
Do not give up.

Remember the steps:
build-essential (linux headers, gcc, make, etc.)
modem driver from intel.com or linmodems.technion.ac.il
patch
make install
copy wvdial.conf to /etc/wvdial.conf and edit
pppconfig


Time permitting I will look up the link to the patch file.  The full name is:
patch-intel-537ep-kernel2611-2.60.80.1-20050528.diff.tar.gz
which you should be able to google yourself.

I pray all goes well for you.

Feel free to PM me with questions, though I am just a gnubie too.  azz and towsonu200* are real experts.

thanks

well, my email came in.  GTG

---

### Post by Su-buntu on 2006-11-14
I realy can`t understan how is it possible not to include drivers for well known modems.Becouse there is so many things that you have to download and install after you install Ubuntu that is so ununderstandable that you need to download with some other OS and than to burn on CD and than to install on Ubuntu. It doesn`t make sens at all. It is realy unpardonable that beginers have to torture  to do something that should be included in first place, and it is supouse to be ,if not very than relativly, simple. To install drivers for modem you have to install a banch of things before.
NONSENSE!!!
I`m trying for a few days and nothing. First of all I can`t install  
g++....the first three (gcc,cpp,...)was sucesfully. When I downloaded the instruction from Intel officioal site how to install I got stocked ona first step "..extract the archive into a directory tar -zxvf <archivename>.tgz". I don`t  understand this where and how to do that.

---

