---
title: "shifting evolution from one computer to another"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2007-12-22
Hi all,

I am using Ubuntu 7.10 and am having problems shifting Evolution from one computer to another. I am following the procedure given in the FAQ:
[url]http://www.go-evolution.org/FAQ#How_can_I_transfer_all_my_Evolution_data_between_computers.2Fto_a_new_partition.2Fto_a_new_computer.3F
[/url]

I first did: 

```
evolution --force-shutdown

```
and got this:

[HTML]Shutting down evolution-exchange-storage (Evolution Calendar Exchange backend / Evolution Addressbook Exchange backend)
Shutting down evolution-data-server-1.12 (Evolution Calendar file and webcal backend / Evolution Addressbook file backend)
Shutting down evolution-alarm-notify (Evolution Calendar alarm notification service)
[/HTML]

Now, when I try to copy the contents from the folder $HOME/.evolution/ into a folder in an external hard drive (/media/IOMEGA/EVOLUTION/)

```
sudo cp -r $HOME/.evolution/ /media/IOMEGA/EVOLUTION/

```
I get the following error messages:

[HTML]cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local#Inbox_R': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local#Inbox': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local#Sent': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local#Drafts': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local#Inbox_Conference': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local#Outbox': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local#Inbox_Econ201': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local#._23evolution_Trash': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local#._23evolution_Junk': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local#Inbox_Fall06': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local#Inbox_Referee': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local#Inbox_Econ520': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local#Inbox_Econ_20444': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local#Inbox_Submissions': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local#Inbox_Econ520_SU07': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-vfolder:_home_basu15_.evolution_mail_vfolder#Account_20Search': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local#Inbox_Job_20Market': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local#Inbox_Econ520_AU07': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local_Inbox': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local_Inbox_Job_20Market': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local_Sent': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local_Inbox_Conference': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local_Inbox_Econ520_AU07': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local_Inbox_Econ520': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local_Inbox_Econ520_WI08': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/config/et-expanded-mbox:_home_basu15_.evolution_mail_local_Inbox_Submissions': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/views/custom_view-mbox:_home_basu15_.evolution_mail_local#Inbox_Econ_20444.xml': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/views/current_view-mbox:_home_basu15_.evolution_mail_local#Inbox_Fall06.xml': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/views/custom_view-mbox:_home_basu15_.evolution_mail_local#Inbox_Fall06.xml': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/views/current_view-mbox:_home_basu15_.evolution_mail_local#Inbox_Econ520_AU07.xml': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/views/current_view-mbox:_home_basu15_.evolution_mail_local#Inbox_Econ_20444.xml': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/views/current_view-vfolder:_home_basu15_.evolution_mail_vfolder#Account_20Search.xml': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/views/custom_view-vfolder:_home_basu15_.evolution_mail_vfolder#Account_20Search.xml': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/views/custom_view-mbox:_home_basu15_.evolution_mail_local#Inbox_Econ520_AU07.xml': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/views/current_view-mbox:_home_basu15_.evolution_mail_local_Inbox_Econ520_WI08.xml': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/mail/views/custom_view-mbox:_home_basu15_.evolution_mail_local_Inbox_Econ520_WI08.xml': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/addressbook/views/current_view-file:___home_basu15_.evolution_addressbook_local_system.xml': Invalid argument
cp: cannot create regular file `/media/IOMEGA/EVOLUTION/.evolution/addressbook/views/custom_view-file:___home_basu15_.evolution_addressbook_local_system.xml': Invalid argument[/HTML]


What is going wrong?

---

### Post by cmnorton on 2007-12-22
Are you trying to move your email from one system to another? Or are you trying to have two systems share the same files?

You should be able to take your ~/.evolution directory, back it up, and unpack it on another system. I did that going from Fedora 6 to Ubuntu 6.06.

---

### Post by kool_kat_os on 2007-12-22
write protected maybe... not enough privileges  ????

---

### Post by aam-aadmi on 2007-12-23
cmnorton,

I am trying to move from one computer to another, exactly what you did. Could you tell me what you did in a little more detail? That would be of great help.

I am guessing this is what you did (from reading your post):

1. make an archive of all the files and directories in ~/.evolution
2. copy the archive to a media and then to the new machine

3. open Evolution in the new machine and then choose to import files from the saved archive (this option comes up right when you open Evolution for the first time, right?)

OR

3(a) unpack the archive into ~/.evolution in the new machine? and then start Evolution?

Did you do 3 or 3(a)?

---

### Post by enuckon on 2008-05-22
FAT32 file systems cannot use certain characters, like ":", "<", "/" etc. 
Make sure that you replace them before copying.

---

