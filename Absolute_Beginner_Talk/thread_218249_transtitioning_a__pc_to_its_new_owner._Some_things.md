---
title: "transtitioning a  pc to its new owner. Some things to do before I give it"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-07-18
Soon, I'll be giving this computer I'm using to a friend. She will be its new owner.

1) How can I remove all my personal settings/configurations? For example, the panel configuration. I think the default panel configuration is 2 panels. One on the top and one at the bottom. I have changed it. I have just one panel, on the bottom.  I'd like to get this change and all other changes that I've made, as it would be if I have just freshly installed Ubuntu. I don't remember all the changes I've made, because I've  been using Ubunu for about 14 months now.


2) Related to point 1 above: How can I have only the programs that are pre-installed with a fresh install of Ubuntu? I've upgraded from Breezy. I've installed several programs along the way. I don't know which are the pre-installed programs and which are the programs that I installed.


3) How can I remove/clear my account (password) etc on the day the pc makes the transition from me to her? How can I have the computer prompt her, when she turns on the computer for the first time, to enter her new password? 

Or would it be easier if I just create a new account with her name, make a new password for her, and then show her how to change her password? 


4) How can I make sure all the stuff I deleted cannot be recovered? (I think this is called double-wiping.)


5) What other things do you suggest I do to make the transition from me to my friend owner a good transition? Oh, it should be said that my friend has never used Ubuntu or Linux before.

One thing I can think of is giving her specific instructions on setting up the broadband internet connection. For me, this was the scariest jump in making the jump from Windows to LInux: How do I get online? And I can't get online with this computer, how do I get the online help that I need? (My solution was to get help using another computer.) I'm going to tell her to go to terminal and type "sudo pppoeconf". 

Another thing is that I'm going to tell her where to get help: [http://www.ubuntu.com/support/supportoptions/freesupport](http://www.ubuntu.com/support/supportoptions/freesupport)

What other things should she know?

I want to make her feel at ease, especially at first. I want to make sure that she's got everything she needs at just a click away: web browser (firefox), skype, music player (rhythymbox), gaim, openoffice.

---

### Post by John.Michael.Kane on 2006-07-18
Your best bet is to back up your files,and [**[COLOR="Red"]dban[/COLOR]**]("http://dban.sourceforge.net/") the drive. Then reinstall setting it up for her with only the software she needs.

---

### Post by Kilz on 2006-07-18
IMHO you should wipe the hard drive and reinstall the OS of any computer before giving it away. Deleting this and that to get the files with your info on them isnt as relable as a fresh install.

---

### Post by hanzj on 2006-07-18
SD-Plissken, Kilz,
Thanks for your input on Question Number 4.

Somer reasons that discourage me from doing so:
1) I don't have Ubuntu on CD, so doing a fresh install would be tricky. And my PC can't burn onto CDs. It's just got a plain CD-Rom reader.

2) I'd like to use my computer until the day I give it to her.

---

### Post by taurus on 2006-07-18
I assume you know that you can order a Dapper from ShipIt for free, right!!!  It usually takes about 4 weeks but I think the mad rush is over so it may take a little less time now...  Otherwise, order it over the net (with third party) for a minimal charge.

---

### Post by JShadow on 2006-07-18
1) Your personal settings as far as panel etc should be part of your user profile. Create a new user for her and the settings should be default.

2) That would be a little tricky, it might be easier to remove packages that aren't in the main and that would get you pretty close anyhow. Packages in the main have the Ubuntu logo next to them in Synaptic.

3) Create a new user for her.
Delete your user: sudo deluser --remove-all-files username

4) What file system are you using? It's pretty much impossible to recover files from ext3 so I wouldn't really worry about a novice  getting your stuff back. See [http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html](http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html)

5) Make sure codecs are installed for the media she uses. A big problem with new users seems to be the codecs.

---

### Post by hanzj on 2006-07-18
Wow, it takes just 4 weeks now? When I ordered Hoary a year ago, it took many months. I thought it would never come.

I'll be handing the computer next week, so I can't wait for ShipIt.

---

### Post by taurus on 2006-07-18
Then either find a friend who has a fast network connection, check your local library, or get it for a minimal charge!  The last option is your best bet...

---

### Post by hanzj on 2006-07-18
JShadow,

2) Is there a way to do as you say using Terminal?

4) ext3 (according to "mount"). When I accidentally formatted my brother's portable USB hard drive NTFS, I was able to recover all the files with a program. I read the faq link you gave. I hope it won't be that easy to do with EXT3.

---

### Post by JShadow on 2006-07-18
Do the following:

```

sudo useradd --create-home her_user_name
sudo passwd her_user_name 
sudo deluser --remove-all-files your_user_name

```

The first line adds her user to your system and creates a home folder. The second sets her password. The last removes your files and username from the system.

Edit: Sorry, didn't realize you were talking about the packages. That would be quite tedious to do from the CLI. I'd just use Synaptic.

---

### Post by hanzj on 2006-07-18
Actually,
my "2)" was referring to your "2)"... about using terminal to remove packages without the Ubuntu logo in synaptic. But I'm glad you told me how to do the username/password thing in terminal. 

I'll be telling her about her temporary password (what I've set up). I'll also suggest that she change her password. She can make up her new password by going to  System/Administration/Users and Groups.

---

