---
title: "how much space for linux swap and hda needed"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by tony2 on 2006-12-17
i have approximate space of 20 GB free for Ubuntu. Now I am installing Ubuntu 6.10. how much space i need to specify for linux swap and extension3. Your response needed.

---

### Post by zgornel on 2006-12-17
I'd recommend a 8GB for** /** (ext3), 11GB for **/home** and 1GB **swap**. If you have more than 1GB of ram, make swap at least the same size as the amount of memory installed.

---

### Post by tony2 on 2006-12-17
i have 500 mb ram. i am confused at the step 5 of installion. I dont know which one to select. Can you help me?

3 options are given

1. erase entire disk ide1 80 GB

2. use the largest continuous free space

3. manually edit partition table

which one to select?

---

### Post by dannystaple on 2006-12-17
> **tony2 said:**
> i have 500 mb ram. i am confused at the step 5 of installion. I dont know which one to select. Can you help me?

Remind us what step five is again and we can probably help you, I am sure I am not alone in never memorising what happens at numbered steps..

---

### Post by tony2 on 2006-12-17
update: the options are shown in the post 3

zgornel - how to partition like that.

---

### Post by bulldog on 2006-12-17
Take manual partitioning.
Than create in the free space a swap 1GB
A root  / partition 8GB
A home /home partition from the rest of the space.

Set to format swap as swap,/ as ext3 and your /home ext3 as well and apply and continue the install.
Take a good look no one of your windows partitions are set to format!!

---

### Post by dannystaple on 2006-12-17
> **tony2 said:**
> update: the options are shown in the post 3

zgornel - how to partition like that.

Thanks, okay - are you looking to dual boot, or make with a clean install?

The first option is for a completely clean install, and will completely erase the disk, not just a single partition. 

If you already have data on the drive you want to keep, and you have actually got unpartitioned space to use, then option 2 is for you.

Option 3 is probably not what you want, as this allows you to get right in and manually edit the partitions and go with your own configuration - not something for the newbie.

---

### Post by tony2 on 2006-12-17
i selected manual partition and gparted has started. its is showing that there is already a linux swap of 86 MB.

danny i have windows for 40 gb. i need dual boot of windows and linux.

---

### Post by msandersen on 2006-12-17
> **tony2 said:**
> i have 500 mb ram. i am confused at the step 5 of installion. I dont know which one to select. Can you help me?

3 options are given

1. erase entire disk ide1 80 GB

2. use the largest continuous free space

3. manually edit partition table

which one to select?
1. If you are dedicating the entire hard drive to Ubuntu, this will, as it says, erase the entire hard drive and use that. Probably not what you want.

2. If you already have free unformatted space, say if you've used a Windows partitioner like Partition Magic, this option can use that.

3. Use the built-in partitioning tool to repartition the hard drive for dual-booting with Windows or any other OS. As you only want 20Gb for Ubuntu, this is probably the option you are looking for. This is where you can resize the Windows partition to make room for Linux and set up the partitions mentioned above; root /), Home (/home), and Swap. It is possible to set others, but it's not needed. Home is optional too, but it is good practice to have a separate Home partition, so you can reinstall without damaging your personal data.

Either way, **BACK UP FIRST!** Partitioning messes with your hard drive on a fundamental level, and there has been problems with the partitioner before, where people haven't been able to log into Windows after, and it's tricky to fix.

---

### Post by tony2 on 2006-12-17
i do not understand what is happening. i deleted swap, ext etc and it is showing only 40 gb and 11 gb. can u tell me how to create a screenshot in ubuntu so that i can post a screenshot so that it would easier for you to understand.

---

### Post by Delkster on 2006-12-17
> **tony2 said:**
> can u tell me how to create a screenshot in ubuntu so that i can post a screenshot so that it would easier for you to understand.

Press the PrintScreen button on the keyboard.

---

### Post by tony2 on 2006-12-17
Installed Ubuntu using 2nd point of 9 th post in this thread. I need to listen to music online using real player. is there a way ? 

thanks for your reply.

---

### Post by dannystaple on 2006-12-17
> **tony2 said:**
> Installed Ubuntu using 2nd point of 9 th post in this thread. I need to listen to music online using real player. is there a way ? 

thanks for your reply.

Hi Tony,
You should probably start a new thread for that, but anyway, first question - why real player? You can listen to online music with any number of music players, and I would probably recommend Amarok over RealPlayer.  Either way, you will need to enable the restricted repository, and make sure you get mp3 playback. Start synaptic with system->Administration-Synpatic Package manager, you will probably need to type your password at this point, then after it is open click on Settings->Repositories. Enable Universe, Multiverse and Restricted if they are not already. Unless you want to keep reaching for the CD-ROM, then now is good time to disable the CD/DVD roms from the list below.

Click Close, then it will prompt you to reload, click through the dialog and click the reload button on the toolbar. 

Again - Realplayer is not your best option unless you are specifically trying to play real media. There is Rythmbox (Simple, a little like iTunes), XMMS (Like winamp - has everything except smart playlists) and Amarok (quite customizable and has smart dynamic playlists) as well as realplayer if you really need it. You will want to follow the instructions [here](https://help.ubuntu.com/community/RestrictedFormats) for info on how to set up the MP3 codec itself, as well as having more info on the media players.

---

### Post by tony2 on 2006-12-17
i will try amarok. i am not a fan of real player either. thanks. 

whenever i open firefox to access gmail it shuts down. i do not know why it happens. any idea?

---

### Post by jamespi on 2006-12-17
do you mean firefox quits whenever you visit gmail? or does it quit everytime you open it up?

try opening a command terminal (applications->accessories->terminal) and just type firefox to load firefox. then go to gmail and see if it print out any useful error messages in the terminal when it quits.

also do you have any extensions (or add-ons as they are now called) installed in firefox? try deactivating or uninstalling them. then try turning off javascript and see if that stops it crashing. i imagine since gmail is an AJAX website it will require javascript but it would be helpful to eliminate it as a cause.

---

### Post by tony2 on 2006-12-17
yes, firefox quits when i try to login to gmail. even with no extensions firefox quits when i login to gmail.

---

### Post by jamespi on 2006-12-17
did you try the terminal thing mentioned?

---

### Post by tony2 on 2006-12-17
yes i tried opening firefox using the terminal but even then firefox quits.

it doesn't quit only when i disable javascript. but do you think browsing without javascript would be better?

---

### Post by jamespi on 2006-12-18
you could install the noscript extension - that allows you to whitelist sites that you want to use javascript on. that way you can have javascript on when you need it, or not when it's a problem.

when it quit after you'd run it from the terminal, were there any error messages printed to terminal?

---

