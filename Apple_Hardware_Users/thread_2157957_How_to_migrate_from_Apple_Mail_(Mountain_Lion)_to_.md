---
title: "How to migrate from Apple Mail (Mountain Lion) to Thunderbird 17?"
date: 2013-06-27
forum: Apple Hardware Users
---

### Post by PartisanEntity on 2013-06-27
Hi everyone,

I have been using Apple Mail for a while now, I have several accounts set up and also many folders.

I would like to migrate everything to Thunderbird.

So I thought I would do the following:

[LIST]
[*]- Install Thunderbird on Mac
[*]- Migrate everything from Apple Mail to Thunderbird on Mac
[*]- Export everything from Thunderbird on Mac
[*]- Import to Thunderbird on Ubuntu
[/LIST]


First obstacle:

[LIST]
[*]- Thunderbird Import feature tells me it could not find any folders to import from Apple Mail.
[/LIST]


After some reading, it seems that Apple changed the way the .mbox folders work.

Anyone run into this too? Any easy solutions that won't take me a week to complete? (My archive dates back to 2002).

---

### Post by PartisanEntity on 2013-06-27
If anyone runs into the same situation here is what I found out and a solution:

As of version 4.5 of Apple Mail, emails are no longer stored in the real *.mbox format that many email clients understand. Instead, inside this pseudo *.mbox folder, each email is stored as a seperate *.emlx file (Apple did this so that emails can be indexed and found through a Spotlight search).

This means the built in Import feature in Thunderbird 17 doesn't work anymore (at least as far as OSX and Apple Mail are concerned).

The solution:

The solution requires several steps.

You can install an addon for Thunderbird called ImportExportTools.

This tool can import the individual *.emlx files into Thunderbird, BUT:

The next issue is that if you store your emails in folders and subfolders in Apple Mail, then your *.emlx files will for some strange reason be stored in countless subfolders within subfolders within home/user/yourname/Library/Mail/ (. So you would need millions of years to go through each one and use the addon ImportExportTools to import them all into Thunderbird.

I have all my emails since 2002, I was going to cry.

Until I came across the idea of using Automator in order to create a script that copies all *.emlx files from folders and their subfolders to a location you specify.

This way at least you don't have go through thousands of folders and instead you can drag and drop the main *.mbox folder on to you Automator script and it will go through all the subfolders and copy the *.emlx files to a location you specify.

Then finally you can use ImportExportTools to import the emails into Thunderbird (or into various folders in Thunderbird).

Phew, hope I have not lost you.

But this is working right now.

---

### Post by cyberdork33 on 2013-06-27
In Apple Mail, select the mailboxes you want to export. Go to the menu and choose Mailbox > Export Mailbox

Mail exports mailboxes into a container with an .mbox extension, but they are not true mbox format, they are actually a folder. Double-Click to open the folder and there is a file with only "mbox" as its name. This is the real mbox file for that mailbox.

With the ImportExportTools extension in Thunderbird though, you can use Tools > ImportExportTools > import mbox file
Then tell choose the option to pick and directory and search it for mbox files. each of the mailbox mbox files you exported from mail can then be imported into its own folder in Thunderbird.

I used to use the Mail Scripts' Archive tool to export email from Apple Mail, but it is not really being developed any longer.
[http://www.andreasamann.com/MacOSX/Mail_Scripts](http://www.andreasamann.com/MacOSX/Mail_Scripts)

---

### Post by PartisanEntity on 2013-06-28
Thanks very much for the suggestion. I will have to try your method. I used my method however last night and went through all my folders and migrated all my emails to Thunderbird, it took ages :)

---

### Post by cyberdork33 on 2013-06-28
I've actually done this too many times and have now setup a imap server locally on my Mac with dovecot as my archival location for email. That way, I can just setup a normal imap account in any client and my email is there.

---

### Post by PartisanEntity on 2013-06-28
Oh my God that is such a clever idea! I have no experiences at all with setting up an imap server, but I will definitely look into this. Any tutorials or HowTos you recommend for someone who knows absolutely nothing about email servers?

p.s. how do you add new emails to this imap archive though ? Using your email client? (i.e. drag them to the imap folder?)

---

### Post by cyberdork33 on 2013-06-28
[FONT=arial]Yea. You got the idea...

I just read alot and figured out something really simple since it shouldn't be accessible outside my local machine.

Here is my config file.

&#8203;```

# Only need imap protocol
protocols = imap
listen = 127.0.0.1


# Logs
log_path = /var/log/mail.log
info_log_path = /var/log/mail.log


# Disable SSL
ssl = no


# Fancy mbox config that supports subfolders
mail_location = mbox:~/mailboxes:DIRNAME=mBoX-MeSsAgEs:INDEX=~/index:CONTROL=~/control


# Authentication configuration:
#auth_verbose = yes
auth_mechanisms = plain
passdb {
  driver = passwd-file
  args = /usr/local/etc/dovecot/passwd
}
userdb {
  driver = static
  args = uid=username gid=group home=/Users/username/imap

}
```

The passwd file looks like this:
```
mailserverusername@localhost:{PLAIN}mailpassword
```[/FONT][FONT=courier new]
[/FONT]

---

### Post by duke2 on 2013-08-14
Hi Partisan,

Ive found this thread whilst searching for a solution for my Mac Mail dilemma which is very similar to the one you were having. Being a total noob at Automator as well as the world of emails I was wondering if it was possible for you to share the Automator action that i can run.

Im having issues with my many devices creating errors on the 4 hosted websites of my businesses:

 As Host Gator have provided a solution to "If you receive an error regarding "too many connections" or "error  500", you have a couple of options. If neither one solves your problem,  please contact HostGator Support for assistance.

 1. Try a different mail client. We recommend Mozilla Thunderbird because it's stable, easy to use, and freely licensed.

etc...


So here I am thinking that it would be an easy solution to migrate to TB , but am getting stuck in email hell because of Apple's change.

I have multiple email accounts and it seems that TB is the way to go. If you could please explain what is happening in the action I would be extremely grateful also. Looking forward to a solution and thank you!!! 

Best

---

