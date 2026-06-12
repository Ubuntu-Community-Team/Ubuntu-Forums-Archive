---
title: "Clamav and lost emails"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by panorack on 2008-04-09
Because I dual boot with Windows XP (for propriety software that I cannot find for Linux) I recently installed ClamAV with Synaptic. I use Evolution for my emails but could not find a way of integrating the AV program with it.

Following advice in 'Ubuntu Hacks' (Hack #73) I set up a directory, '/tmp/virus'  to move any infected files to and ran [I]clamscan[I] recursively from my Home directory with the option to move infected files to the temporary directory set up. This showed two files with 'Phishing.Bank' in the file. One of these in the Inbox and one in the Sent items. I had received a phishing email some time ago and I sent a copy to the bank concerned so although I thought Clam AV should not flag the word 'phish' the result encouraged me to do a full scan overnight as a cron job.

'Ubuntu Hacks' referred to adding a line to '*/etc/crontab'[I]. I could not find this directory but [I]/etc/cron.d* contained a text config file 'anacron' using the same format so I used that believing the difference to be changes in later versions of Ubuntu. The following is the line I added to the 'anacron' file:
**11 3 * * * root mkdir /tmp/virus ; clamscan -ri --log=/var/log/clamscan.log --move=/tmp/virus /** 

On loading Evolution the following day both the Inbox and Sent box were empty and a search has provided no clues as to the whereabouts of these files.:(

1. Can anyone offer any help as to what has happened to these emails - and can I retrieve them?

2. I would still like to scan incoming emails as I have a number from Windows machines and some with attachments. Can anyone tell me how to get Evolution to use ClamAV for this job?:confused:

---

