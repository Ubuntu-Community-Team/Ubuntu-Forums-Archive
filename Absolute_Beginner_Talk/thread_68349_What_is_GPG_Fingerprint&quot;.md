---
title: "What is GPG Fingerprint&quot;"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by Benchrest on 2005-09-22
Message -- "Key Fingerprint
Paste the Key Fingerprint (use: gpg --fingerprint YOU, can only be used with v4 keys). Launchpad will send a message to [email]xxxxx@xxx.net[/email] containing the instructions to conclude the process."

I am trying to create an ID in launchpad so I can get breezy mailed to me when it's available instead of downloading like I did for Hoary. I guess I'm some kind of dummy cause I haven't the faintest idea what this message is talking about. I don't know what gpg is. I don't know what v4 keys are, or what a Key fingerprint is. I read the code of conduct but it doesn't give me a key that I read it. Launchpad doesn't seem to have anyway of asking a question, only reporting a problem.  Any help would be appreciated.

---

### Post by bsussman on 2005-09-22
Gpg is a generator of conformant public key / private key information, used in very secure systems, especially since it is a meethod by which folks can prove that you digitally signed something.

start reading here - [size=-1][color=#008000][www.gnupg.org]("http://www.gnupg.org")



[/color][/size] ```
 >gpg --fingerprint Your Name
``` [size=-1][color=#008000]

produces a dump of some of your pub key/pvt key data, including your fingerprint.[/color][/size]
[size=-1][color=#008000]

[/color][/size]

---

### Post by Benchrest on 2005-09-22
Thanks for your reply. I suspected it it was some kind of security key. I went into SHIPIT again and used the user ID and password I had set up and it let me order the CD's without having finished the GPG key setup. Maybe I got there erroneously and the GPG key is only required for persons who want to write code etc.? Anyhow I got my order placed. Perhaps it would have been easier if I had been on my Ubuntu machine, but I don't have the laptop on all the time. Loading the required program might have been easier than on this windows desktop. The [www.gnupg.org](www.gnupg.org)  web site has a link to installing on windows that doesn't work. Rich

---

### Post by bsussman on 2005-09-22
I think SHIPIT has an 'I am  paranoid' option and this is what you stumbled into....

happy UBUNTUing

---

### Post by az on 2005-09-22
Yeah, I do not think you need to sign the code of conduct to order shipit cds....



But if you still want to sign to code of conduct to become a member of the ubuntu (to get involved with the ubuntu community council) read this:

[https://wiki.ubuntu.com/GnuPrivacyGuardHowto](https://wiki.ubuntu.com/GnuPrivacyGuardHowto)

---

