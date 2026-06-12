---
title: "importing/upgrading from win XP"
date: 2005-06-14
forum: Absolute Beginner Talk
---

### Post by daniel@dpr on 2005-06-14
Hi there,
Couldnt find a definitive "transfer files and settings" from win xp instrunction manual, so im posting a few queries as i have never done this before.
I wish to move (upgrade) to Ubuntu.

I am currently using windows xp (condolances accepted) on my laptop. I use office2003, and outlook2003 for my mail.

I would love to be able to transfer my email accounts and settings, if not, just all my emails and the folder structure. Any ideas on how to do this?

Also, all my files etc. I am thinking that all i have to do is copy everything to a dvd or 3, then just copy those back once i have Ubuntu up and running?

Finally, how do i get my favourites across?

Or, do i install firefox, using the transfer settings feature, and somehow back up the favourites in that? Maybe i should do the same for thunderbird emails. i know i can install it and it transfers from outlook everything, maybe i should do that and back that up for when i set it or evolution (whichever is better) up in ubuntu?


I do have another PC running Xp, and i have tested the live version on both laptop and PC and all seems ok. So what i thought was i set up ubuntu on the pc, transfer everything over to see if its possible, then transfer it all back to my laptop after a fresh and clean (reformatted) installation of ubuntu?


So any ideas on how to get or keep my data (mainly word docs, pictures, excel and other files)
Thanks

---

### Post by monchichi on 2005-06-14
Hi,

Try [OpenMoveOver](http:///openmoveover.sourceforge.net/)! I haven't tried it (not having any Windows machines for a few years), but I heard good things about the commerical product it is modeled after, [MoveOver](http://www.resolvo.com/moveover/).

Post back here if you have any trouble!

---

### Post by costoa on 2005-06-14
Daniel,

Lots of issues here which will take a few back-and-forth postings.  Unfortunately there is not yet a simplified means for switching from MS XP to GNU/Linux. Partly because MS purposely makes it somewhat difficult to access data files created with their software and partly because writing the tools to correctly convert said data is also difficult. FOSS apps, by their very nature, use open data formats which makes it easy to switch between different email, web browsers, spreadsheet, etc. apps. 

I'll make the assumption that you have some means of backup your personal data (i.e.: cdr, usb flash drive, etc.). You mentioned backing up to dvd which is fine. Ubuntu should have no problem mounting it.

Before getting into the dirty details if you have XP Pro and a static connection to the Internet you can use "remote desktop" to connect to your desktop (running XP Pro) from you laptop (running GNU/Linux). Ubuntu* has a command line program called rdesktop and a GUI frontend for rdesktop called tsclient. tsclient is very similar to MS' Remote Desktop Client. I use both everyday and they work great. Post if you need information on setting up RDP (Remote Desktop Protocol) on MS XP Pro. BTW, RDP is a feature of XP Pro and is not included with XP Home.

Exporting IE bookmarks: Thankfully MS made this easy. In IE go to File -> Import/Export and select "export bookmarks". This will convert your IE bookmarks to a single html file which Mozilla can import without a problem.

Office data files: The quick and incomplete answer is save all these files in an "Office 97" compatible format which OpenOffice can access. This will work for most files but might not with MS Office files that depend on Visual Basic to process data. Normally this isn't an issue but you should be forewarned.

Outlook: What works for me is using Mozilla Suite's email program to import Outlook messages, contacts and settings then backing up your Mozilla folder. After that backup your Mozilla data folder. If you're connecting to an exchange server you'll need to reenter your settings (and use Evolution). 

I'm sure other questions will come up so feel free to post them. Generally speaking moving from MS XP to Ubuntu is pretty smooth. Setting up power management in laptops sometimes takes a little work


Costoa


* For the most part when I say "Ubuntu" I also mean many other GNU/Linux distributions. The reason I use Ubuntu at home, migrated some of the PCs at work (with more to come) from MS XP to Ubuntu and recommend it is because IMO it's the best "polished" distro. Ubuntu is a great distro for people that want a painless installation, setup and use. Some distros (like Gentoo, an excellent distro) are like an old VW type I; major tweaking makes for an ultra smooth and svelte machine. Some distros (like Ubuntu) are like a 1973 Lincoln Continental Coupe; fast, smooth, fun to drive and will run forever with very little maintaince. 

There is no "one" distro that's the best if you have fairly modern hardware (PIII or better) Ubuntu is a great way to go.

---

### Post by aysiu on 2005-06-14
Here's what you should do:

Back up all your files on DVD.

If you're using Outlook, install Thunderbird for Windows. It will offer to import your Outlook settings. If you're using Internet Explorer, install Firefox for Windows. It will offer to import your IE settings.

Then, go to your c://Documents and Settings/*your name*/ folder. Go to Tools > Folder Options > View and click on "Show Hidden Files and Folders." A folder called "Application Data" should appear. Inside of that folder should be two folders: Mozilla and Thunderbird, with Firefox and Thunderbird settings, respectively. Copy both of these folders to your DVD backup.

Once you've installed Ubuntu and installed Firefox and Thunderbird, show hidden files in your home directory and copy your settings to the hidden .mozilla-thunderbird and .mozilla folders.

Honestly, though, I've found copying settings folders a little mucky. Sometimes, it works. Other times, it doesn't. If you want to cleanest transition, create a new email account (it doesn't actually have to be new--it's just a new account as far as your email client is concerned) in Outlook or Thunderbird and make sure it's IMAP (not POP). Drag all your downloaded POP messages into the IMAP account, wait for them to upload. Then, when you start Thunderbird in Ubuntu, just set up your IMAP account.

If you're unfamiliar with this terminology, IMAP maps what you see to what's on the server. Any messages it downloads to your computer it downloads only temporarily. If you move something from your inbox to the trash, it will take the message from the inbox on your mail server and put it in the trash on your mail server. POP downloads messages from your mail server to your actual home computer. You can choose to keep copies on the server itself or not, but you will have actual messages on your actual computer. If you move something from your inbox to the trash, it will go into the trash on your computer, not the mail server.

The advantage of IMAP is that your messages and where they are will be the same wherever you go, wherever you check your email from. This is particularly handy if you're migrating computers, changing operating systems, or if you often check your email from several different computers.

The advantage of POP is that it's faster. Since the messages live on your computer, you can scroll through them and move them around more quickly. Also, if you have many messages with large attachments, your mail server may not let you keep them all on there unless you pay more money.

For "favorites," I'd install Firefox, have it import the favorites automatically. Then go to Bookmarks > Manage Bookmarks > File > Export. It will save your bookmarks as *bookmarks.html*. If you put that on your DVD backup, you can use that same method (Bookmarks > Manage Bookmarks > File > Import) to get your bookmarks back in the Ubuntu Firefox.

Any other "settings" (besides bookmarks/favorites and emails) will likely not be applicable in Ubuntu, as you have far more (and different) control over your environment in Linux and Firefox.

---

### Post by naisan on 2005-06-18
Here's what I did:
1) used thunderbird (you can get it from the mozilla.org site - it is the email client for firefox browser) running on windows to import from my .pst file that had my outlook 2003 email
2) copied the resulting data from the \windows\docs and settings\user\thunderbird folder into a folder that I share with linux (like a fat32 partition)
3) that is a bunch of mbox folders which you can use o2e (google "o2e" for the site) which is a linux script that takes the mbox email and reformats it for evolution
4) move it to the evolution folder for user and you're done.

you can get better instructions on using o2e from that site.

---

### Post by daniel@dpr on 2005-07-04
[QUOTE=naisan]Here's what I did:
1) used thunderbird (you can get it from the mozilla.org site - it is the email client for firefox browser) running on windows to import from my .pst file that had my outlook 2003 email
2) copied the resulting data from the \windows\docs and settings\user\thunderbird folder into a folder that I share with linux (like a fat32 partition)
3) that is a bunch of mbox folders which you can use o2e (google "o2e" for the site) which is a linux script that takes the mbox email and reformats it for evolution
4) move it to the evolution folder for user and you're done.

you can get better instructions on using o2e from that site.[/QUOTE]


Ok, first thanks very much. I have since undertaken the move and all has gone pretty smoothly.
i had problems with the email. I did as was suggested, using thunderbird to get all the folders and emails. To get it working i had to actually copy the "profile" and then create a new profile and point it to that folder, it worked fine from then on.

The export favourites (bookmarks) to html then import again worked great, thanks.

I have enjoyed everything else, got gftp working for my website work etc, found and installed codecs for totem, it plays better now but not everything, i will look into this further.

What i am a little stuck with is various programs that are "windows only". my accounting package is one it seems, it only has an exe file to run it.
is there a way that this can be run in linux?

Other than that issue, im pretty happy with everything.

I operate an online business selling computers and IT hardware (in australia) and am setting up a links page. I would like to say on it that "this business is powered by ubuntu " or something to that nature. is there any policy against this?

I dont want to post the website as it may be considered commercial advertising, i just want to promote Linux a bit more thats all, even though i do sell windows software, i dont think i will use it again.

Thanks to all that helped above, its been a relatively smooth transaction and learning curve this far.

Daniel

---

### Post by aysiu on 2005-07-04
[QUOTE=daniel@dpr]
What i am a little stuck with is various programs that are "windows only". my accounting package is one it seems, it only has an exe file to run it.
is there a way that this can be run in linux?
[/QUOTE] It depends. You can try Wine. That's in the repositories, so you can Synaptic or apt-get that. Otherwise, there's Win4Lin and Crossover Office, but you have to pay for those.

---

