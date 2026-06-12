---
title: "gpg encryption/decryption error"
date: 2013-01-19
forum: Any Other OS
---

### Post by sradithya on 2013-01-19
We are receiving the below error message when trying to encrypt or decrypt a file on AIX server :

gpg: out of  memory while allocating 8192 bytes

gpg process was working for years on the server until the day we started to see this.

This same gpg encryption is working on an other AIX server in the same environment. Many options were tried including copying the gpg from the server thats working on, recycling the server etc. But the error is persisting.

Please post any suggestions that you may have.

---

### Post by mike acker on 2013-01-19
> **sradithya said:**
> We are receiving the below error message when trying to encrypt or decrypt a file on AIX server :

gpg: out of  memory while allocating 8192 bytes

gpg process was working for years on the server until the day we started to see this.

This same gpg encryption is working on an other AIX server in the same environment. Many options were tried including copying the gpg from the server thats working on, recycling the server etc. But the error is persisting.

Please post any suggestions that you may have.

my guess : this is probably one of those error messages that mis-reports the actual problem .  

isolate trouble : what has been recently added/changed ? is it just 1 particular key that is causing trouble ? or one particular message ? 

did you recently add any keys ? if so, try restoring the keyrings 

does GPG function normally when you try --list-keys , --list-key , etc ?

what does cat /proc/meminfo show for free memory ??

better:  use the
```
free -m
```

---

### Post by sradithya on 2013-01-19
We had a server crash recently and it was brought up. Many of the file systems had to be restored.

This is not a problem with any one specific id or a group of id's. Any id trying to encrypt/decrypt is getting this error. Hence this is observed at a server level and not at a user or id level.

We haven't added any keys or key rings recently. This process was working just fine on our server since 2004. All if a sudden we started to see this error.

We had server reboots in the past, but didn't face this problem before.

We tried restoring the file system having gpg from the back ups and from an other server where it is working , but it still didn't help.

We have an other server with identical settings where it is working normally. Even restoring the file system from this server didnt help

---

### Post by sradithya on 2013-01-19
It was functioning for a day after the server crash recovery. Only from the day after this problem is observed.

We still think the key rings are authentic. We tried creating new ids and keyrings and tried the encryption. It even fails for a newly created id.

The server memory is just fine and is well within limits. Even trying to encrypt / decrypt an empty or a 3 record file is facing a problem, hence its irrespective of the file size or who is trying to encrypt/decrypt it.

We suspect that the gpg is trying to make a system call that is failing, but not sure where to look out for.

---

### Post by mike acker on 2013-01-19
> **sradithya said:**
> It was functioning for a day after the server crash recovery. Only from the day after this problem is observed.

We still think the key rings are authentic.

We tried creating new ids and keyrings and tried the encryption. It even fails for a newly created id.

i remember seeing a similar problem on a server with PGP . Tech Support upgraded the server, and then the PGP error message complained of a missing licence code . re-installed the licence and then it was OK

now in Linux there are bunches of these little . pointers -- aliases that have to point to the right places . not knowing what all pointers are required or what they are supposed to point to -- i would want to remove the software and re-install it ... with the hope that the install process would reset everything properly ...

is the software working at all ??  i.e. can you do the --list-keys function ?
```

$ gpg --list-key acker
pub   2048D/364301C7 2010-12-21 [expired: 2012-03-20]
uid                  Mike Acker <mike_acker@charter.net>

pub   2048R/D08880C3 2012-04-20 [expires: 2013-04-20]
uid                  Mike Acker <mike_acker@charter.net>
sub   2048R/C4DF2CD0 2012-04-20 [expires: 2013-04-20]

```

list-keys -- will display all the keys

---

### Post by sradithya on 2013-01-19
Yes I am able to list the keys :

gpg --list-key sradithyapub  1024D/9REA9F0 2013-01-18 sradithya (Hi) <sradithya@abc.net>
sub  1024g/8CF93A9 2013-01-18

Yes, we did a restore of the gpg from back ups and and reinstall and even a server recycle. But it still didnt help.

/home>touch simple1
/home >chmod 777 simple1
/home >/opt/TWWfsw/gnupg12/bin/gpg --encrypt-file simple1
You did not specify a user ID. (you may use "-r")
 
Enter the user ID.  End with an empty line: sradithya
gpg: out of  memory while allocating 8192 bytes
/home >

We wonder if the gpg is making an other system call thats failing with the space problem and if its not an issue with gpg at all.

---

### Post by cariboo on 2013-01-19
Did you run fsck on the system, after the crash? If you didn't, that could be the cause of your errors.

---

### Post by sradithya on 2013-01-19
> **cariboo907 said:**
> Did you run fsck on the system, after the crash? If you didn't, that could be the cause of your errors.

Thank you.

An fsck should have been run on my server after the crash and I am quite positive on that.

Would that span across all the file systems on the server and could anything have been missed? Can we do that selectively on a file system and see if it helps? Does it cause any downtime?

---

### Post by cariboo on 2013-01-19
Usually fsck is only run on / unless specified otherwise, much depends on how you have the system partitioned.

The reason I asked, is I played with fakeraid several years back, and was having a data corruption problem, similar to what you are seeing, unfortunately the fakeraid array was mounted on a different partition from /, so fsck had to run on it manually.

---

### Post by sradithya on 2013-01-19
> **cariboo907 said:**
> Usually fsck is only run on / unless specified otherwise, much depends on how you have the system partitioned.

The reason I asked, is I played with fakeraid several years back, and was having a data corruption problem, similar to what you are seeing, unfortunately the fakeraid array was mounted on a different partition from /, so fsck had to run on it manually.

I am working more on the application end, but i am very positive that a fsck has been executed on the server post crash recovery.

The issue that surprises is that it also worked for a day after the crash recovery. Its only the next day that it stopped working.

No visible changes happened in that one day nor any new file systems were restored. The fact that it worked for a day after crash and then lost is perplexing.

Probably some file system or a library has been corrupted or what could be causing this "gpg: out of  memory while allocating 8192 bytes" error is bothering us.

All the file systems has sufficient memory and this error is seen irrespective of the file size. Even for an empty file we get the same error.

---

### Post by mike acker on 2013-01-20
> **sradithya said:**
> Yes I am able to list the keys :

gpg --list-key sradithyapub  1024D/9REA9F0 2013-01-18 sradithya (Hi) <sradithya@abc.net>
sub  1024g/8CF93A9 2013-01-18

Yes, we did a restore of the gpg from back ups and and reinstall and even a server recycle. But it still didnt help.

/home>touch simple1
/home >chmod 777 simple1
/home >/opt/TWWfsw/gnupg12/bin/gpg --encrypt-file simple1
You did not specify a user ID. (you may use "-r")
 
Enter the user ID.  End with an empty line: sradithya
gpg: out of  memory while allocating 8192 bytes
/home >

We wonder if the gpg is making an other system call thats failing with the space problem and if its not an issue with gpg at all.

it's probably not gpg that's causing the problem then, particularly as it can do --list-keys . which means it most likely finds your key... the next step will be the call to 3DES

i did some tests and poked around a little... and found this page:
[http://www.gnupg.org/documentation/manuals/gnupg-devel/GPG-Esoteric-Options.html](http://www.gnupg.org/documentation/manuals/gnupg-devel/GPG-Esoteric-Options.html)

try
```

gpg --degug-all -r sradithya -e simple1

```then browse thru the messages for clues ...

it is possible to alter the block cipher that is used ... generally gpg will look thru the recipients' keys.... each key specifies a prioritized list of acceptable ciphers .  gpg will select the first one common to the various recipients from your list of supported ciphers.

to  see your prioritized list of supported ciphers:
```

gpg --version

Supported algorithms:
Pubkey: RSA, RSA-E, RSA-S, ELG-E, DSA
Cipher: 3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH, CAMELLIA128, 
        CAMELLIA192, CAMELLIA256
Hash: MD5, SHA1, RIPEMD160, SHA256, SHA384, SHA512, SHA224
Compression: Uncompressed, ZIP, ZLIB, BZIP2

```if the trouble is in the 3DES block cipher you might get around it as follows
```

gpg --cipher-algo CAST5 -r sradithya -e simple1

```CAST5 should be the cipher used to protect your keyring -- which -- we would think is working -- as you are able to --list-keys ok ...

anyway, let us know what hits

---

### Post by sradithya on 2013-01-20
> **mike acker said:**
> it's probably not gpg that's causing the problem then, particularly as it can do --list-keys . which means it most likely finds your key... the next step will be the call to 3DES

i did some tests and poked around a little... and found this page:
[http://www.gnupg.org/documentation/manuals/gnupg-devel/GPG-Esoteric-Options.html](http://www.gnupg.org/documentation/manuals/gnupg-devel/GPG-Esoteric-Options.html)

try
```

gpg --degug-all -r sradithya -e simple1

```then browse thru the messages for clues ...

it is possible to alter the block cipher that is used ... generally gpg will look thru the recipients' keys.... each key specifies a prioritized list of acceptable ciphers .  gpg will select the first one common to the various recipients from your list of supported ciphers.

to  see your prioritized list of supported ciphers:
```

gpg --version

Supported algorithms:
Pubkey: RSA, RSA-E, RSA-S, ELG-E, DSA
Cipher: 3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH, CAMELLIA128, 
        CAMELLIA192, CAMELLIA256
Hash: MD5, SHA1, RIPEMD160, SHA256, SHA384, SHA512, SHA224
Compression: Uncompressed, ZIP, ZLIB, BZIP2

```if the trouble is in the 3DES block cipher you might get around it as follows
```

gpg --cipher-algo CAST5 -r sradithya -e simple1

```CAST5 should be the cipher used to protect your keyring -- which -- we would think is working -- as you are able to --list-keys ok ...

anyway, let us know what hits


Thanks for the inputs. 

Please find the results to the above commands :

1) gpg --degug-all -r sradithya -e simple1

When i execute this, i get a long output but below are the points that i found worth mentioning :

gpg: DBG: iobuf-20.0: underflow: req=8192
gpg: DBG: iobuf-20.0: underflow: got=1819 rc=0
 
gpg: DBG: iobuf-19.0: underflow: req=8192
gpg: DBG: iobuf-19.0: underflow: got=908 rc=0

2) gpg --version

/home/.gnupg >/opt/TWWfsw/bin/gpg --version
gpg (GnuPG) 1.2.3
Copyright (C) 2003 Free Software Foundation, Inc.
This program comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details.
 
Home: ~/.gnupg
Supported algorithms:
Pubkey: RSA, RSA-E, RSA-S, ELG-E, DSA, ELG
Cipher: 3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH
Hash: MD5, SHA1, RIPEMD160, TIGER192, SHA256
Compression: Uncompressed, ZIP, ZLIB 

3) gpg --cipher-algo CAST5 -r sradithya -e simple1

/home/.gnupg >/opt/TWWfsw/bin/gpg --cipher-algo CAST5 -r sradithya -e simple1
gpg: checking the trustdb
gpg: out of  memory while allocating 8192 bytes
/home/.gnupg >/opt/TWWfsw/bin/gpg --cipher-algo 3DES -r sradithya -e simple1
gpg: checking the trustdb
gpg: out of  memory while allocating 8192 bytes

Please let me know your thoughts.

---

### Post by mike acker on 2013-01-20
> **sradithya said:**
> Thanks for the inputs. 

Please find the results to the above commands :

1) gpg --degug-all -r sradithya -e simple1

When i execute this, i get a long output but below are the points that i found worth mentioning :

gpg: DBG: iobuf-20.0: underflow: req=8192
gpg: DBG: iobuf-20.0: underflow: got=1819 rc=0
 
gpg: DBG: iobuf-19.0: underflow: req=8192
gpg: DBG: iobuf-19.0: underflow: got=908 rc=0

2) gpg --version

/home/.gnupg >/opt/TWWfsw/bin/gpg --version
gpg (GnuPG) 1.2.3
Copyright (C) 2003 Free Software Foundation, Inc.
This program comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details.
 
Home: ~/.gnupg
Supported algorithms:
Pubkey: RSA, RSA-E, RSA-S, ELG-E, DSA, ELG
Cipher: 3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH
Hash: MD5, SHA1, RIPEMD160, TIGER192, SHA256
Compression: Uncompressed, ZIP, ZLIB 

3) gpg --cipher-algo CAST5 -r sradithya -e simple1

/home/.gnupg >/opt/TWWfsw/bin/gpg --cipher-algo CAST5 -r sradithya -e simple1
gpg: checking the trustdb
gpg: out of  memory while allocating 8192 bytes
/home/.gnupg >/opt/TWWfsw/bin/gpg --cipher-algo 3DES -r sradithya -e simple1
gpg: checking the trustdb
gpg: out of  memory while allocating 8192 bytes

Please let me know your thoughts.

~~~~~~~~~~~~~~~~~
did you do the  free -m command before launching gpg ?
```

:~$ free -m
             total       used       free     shared    buffers     cached
Mem:         15798       4876      10921          0        264       3188
-/+ buffers/cache:       1424      14373
Swap:         7933          0       7933

```

why do you have version 1.2.3 ( dated 2003 )  ?
what version of Ubuntu are you running ?
it may be hard to get help with software that is badly dated 

are you running this on a rather old computer ? I've seen computers produce misleading messages like this when they were old.... and had bad memory in them ...
the symptoms may be ...reporting a different amount of available RAM each time you power up ...

how much memory is supposed to be in the machine ?  what shows on the free -m query ?

---

### Post by sradithya on 2013-01-20
> **mike acker said:**
> ~~~~~~~~~~~~~~~~~
did you do the  free -m command before launching gpg ?
```

:~$ free -m
             total       used       free     shared    buffers     cached
Mem:         15798       4876      10921          0        264       3188
-/+ buffers/cache:       1424      14373
Swap:         7933          0       7933

```why do you have version 1.2.3 ( dated 2003 )  ?
what version of Ubuntu are you running ?
it may be hard to get help with software that is badly dated 

are you running this on a rather old computer ? I've seen computers produce misleading messages like this when they were old.... and had bad memory in them ...
the symptoms may be ...reporting a different amount of available RAM each time you power up ...

how much memory is supposed to be in the machine ?  what shows on the free -m query ?


We are running on AIX 5.3.12.5.

This was installed long back and has been working fine without any issues until the server hard crashed due to a component failure which had to be replaced later.

The system has ample memory across all the file systems and this doesn't seem to be a constraint. As we are getting the same message even for a empty file and  a 6 byte file.

I'm not exactly the server administrator but on the application end. I am not sure if i can run the free -m command due to the constraints.

The server is well maintained and we do not have the RAM fluctuations. Added to this, all the functionalities on the server are working perfectly normal with only exception to gpg.

---

### Post by mike acker on 2013-01-20
> **sradithya said:**
> We are running on AIX 5.3.12.5.

This was installed long back and has been working fine without any issues until the server hard crashed due to a component failure which had to be replaced later.

The system has ample memory across all the file systems and this doesn't seem to be a constraint. As we are getting the same message even for a empty file and  a 6 byte file.

I'm not exactly the server administrator but on the application end. I am not sure if i can run the free -m command due to the constraints.

The server is well maintained and we do not have the RAM fluctuations. Added to this, all the functionalities on the server are working perfectly normal with only exception to gpg.

when they 'recovered' the server: did they just lay down a backup 'image', i.e. restore the entire server all at once ? if so, how was that backup made ? sometimes when an open-file agent is used to create a backup as a single dataset the system is caught in an in-consistent state,-- which i'm a bit concerned could be your issue

AIX is an IBM system. I'm surprised that you are using GPG with that; I'd have thought they'd have insisted on commercial PGP .  for support reasons .

AIX probably has an IBM supplied backup utility which you are probably using . that backup utility might not recognize your GPG software (I'd be surprised if it did ) . as a result it might not put the software back properly during the restore ... the malloc problem might just be a permissions issue.... does that AIX box have RACF installed? it should. is your GPG authorized to allocate memory ? RACF deals with "APF" Authorized Libraries. you GPG may need to run from an APF authorized library and that setting might not have been restored . these are just things to check . and RACF settings should be described in the install notes that came with your GPG .

suggested reading: [http://www.gnupg.org/download/supported_systems.en.html](http://www.gnupg.org/download/supported_systems.en.html)

I did some poking around, regarding GPG on AIX, ... you could be in trouble here as it is not formally supported.  

if this is a critical commercial system I would look for a work-around at this point. particularly as it is 3pm Sunday,...

I'm retired now but the hospital i worked at used PGP for just a handful of users who preferred that

can you re-direct the outputs to a file that you can move to a PC ?  I would use a Ubuntu 12.04 LTS system : it comes with GPG built in but you will have to move the keyrings .  you can do that using command line

at my hospital they asked us to use FTPS rather than PGP . if you are involved in commercial work here I recommend that approach although it takes time to make the changes . 

that is why you may have to look at moving the data from the AIX box to a PC for encryption  . you are probably looking at manual operations, pro tem .

---

### Post by Eglefino on 2013-01-21
I was following as (one year) Ubuntu-user (& 32-years Windows-user) the Community Help Documentation with the title[ GnuPrivacyGuardHowto]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto?action=fullsearch&value=linkto%3A%22GnuPrivacyGuardHowto%22&context=180") at: 
[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

I followed the 'tour' on that page until a moment I didn't how to go further. I've read a lot on the GnuPG-website and in the manual, but in those text isn't in the same way  written as on the Ubuntu.com  I even was tried to write some tags in the search here but that's a real crime to get working that searcher....pfff.

So thats the reason I come here to ask. If you have opened the given url than I stopped 
*'**Using GnuPG to generate a key**'  *After the line with the lamp-icon... with the text 'setting the key in the bashrc'

With number one set (that I understand):
1. Set your key as the default key by entering this line in your *~/.bashrc*.  
     export GPGKEY=D8FC66D2

But what is following I don't understand!! First there is another number one.... (as note).

1. Please note that will be sourced only during your next session, unless you source it manually. 

2. Now restart the gpg-agent and source your .bashrc again: 

killall -q gpg-agent
eval $(gpg-agent --daemon) 
source ~/.bashrc

Number 2, restart the gpg-agent.... how do I restart gpg-agent in Ubuntu 12.04 and must restart it in de terminal (it's not written how, it's left in the brain of 
'JoseeantonioR', the writers/editors of this text ;)).

Can you (s)he help me to follow the same route but more understandable how it works until  the 'Encryption'. Because also with that issue/item, there comes strange text.
P.e. number 3: To create a subkey, enter 'addkey'. Sorry,  I'm not stupid, but this text is in my opinion a little strange written.
I hope that the person which will help me, give me the right steps. After number 7 I will stop and will wait maybe 10 days before to go further (If I don't understand or have another questions I come back).

Sorry for my strange written English translated text (from a dictionary), it's not my language of birth, I learned it perhaps 38-years ago on school :lolflag: ). But with this language I get more answers as in my own language and there is more choice with Ubuntu/Linux fora. I'm bedridden and disabled so take your time for my further dialogues. I'm a happy Ubuntu-user!

---

### Post by mike acker on 2013-01-21
> **Eglefino said:**
> I was following as (one year) Ubuntu-user (& 32-years Windows-user) the Community Help Documentation with the title[ GnuPrivacyGuardHowto]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto?action=fullsearch&value=linkto%3A%22GnuPrivacyGuardHowto%22&context=180") at: 
[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

I followed the 'tour' on that page until a moment I didn't how to go further. I've read a lot on the GnuPG-website and in the manual, but in those text isn't in the same way  written as on the Ubuntu.com  I even was tried to write some tags in the search here but that's a real crime to get working that searcher....pfff.

So thats the reason I come here to ask. If you have opened the given url than I stopped 
*'**Using GnuPG to generate a key**'  *After the line with the lamp-icon... with the text 'setting the key in the bashrc'
{snip}
Sorry for my strange written English translated text (from a dictionary), it's not my language of birth, I learned it perhaps 38-years ago on school{snip}

~~~~~
-- what's your natural language ??  your profile doesn't make a note...
-- what version of Ubuntu are you on? 12.04 or 12.04 LTS . this should be in your profile
~~~~~
first off, what are you trying to do ??  GPG comes with your Ubuntu system and the agent should be active when you start the system

try the basic: From TERMINAL :
```

~$ gpg --version
gpg (GnuPG) 1.4.11
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Home: ~/.gnupg
Supported algorithms:
Pubkey: RSA, RSA-E, RSA-S, ELG-E, DSA
Cipher: 3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH, CAMELLIA128, 
        CAMELLIA192, CAMELLIA256
Hash: MD5, SHA1, RIPEMD160, SHA256, SHA384, SHA512, SHA224
Compression: Uncompressed, ZIP, ZLIB, BZIP2

```you should get the output as shown

if you do then you GPG is ready for use

most likely you want to use it with Thunderbird. Thunderbird also comes pre-installed on your 12.04 system and in  spite of what Kim Kommando sez it's a terriffic e/mail client . to use PGP with Thunderbird active the ENIGMAIL plug-in and then generate your key-pair .  remember to always generate a REVOKE key when you create a new key

there is also an e/mail list : [EMAIL="enigmail-users@enigmail.net"]enigmail-users@enigmail.net[/EMAIL]

you should do most of your GPG work using the Key Management menu in Thunderbird .

---

### Post by oldos2er on 2013-01-21
Moved to Other OS/Distro Talk.

---

### Post by sradithya on 2013-01-21
Truss output from a server where gpg is NOT working :

[FONT=Arial]/home> truss /opt/TWWfsw/bin/gpg --verbose --default-recipient-self --yes --encrypt-files sample2 > truss.out[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]execve("/usr/bin/gpg", 0x2FF2253C, 0x2000FB38) argc: 7[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]execve("/etc/gpg", 0x2FF2253C, 0x2000FB38) argc: 7[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]execve("/usr/sbin/gpg", 0x2FF2253C, 0x2000FB38) argc: 7[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]execve("/usr/ucb/gpg", 0x2FF2253C, 0x2000FB38) argc: 7[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]execve("/home/adwodadm/bin/gpg", 0x2FF2253C, 0x2000FB38) argc: 7[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]execve("/usr/bin/X11/gpg", 0x2FF2253C, 0x2000FB38) argc: 7[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]execve("/sbin/gpg", 0x2FF2253C, 0x2000FB38) argc: 7[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]execve("./gpg", 0x2FF2253C, 0x2000FB38) argc: 7[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]execve("/datastage/adwprod_753_app/Ascential/DataStage/DSEngine/bin/gpg", 0x2FF2253C, 0x2000FB38) argc: 7[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]execve("./gpg", 0x2FF2253C, 0x2000FB38) argc: 7[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]truss: 0915-007 Lost control of process.[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]gpg: using secondary key DFEEFFE instead of primary key 97SDFERF4[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]gpg: reading from `sample2'[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]gpg: writing to `sample2.gpg'[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]gpg: ELG-E/AES256 encrypted for: "D8C00BBB test01 (test ods) [/FONT]
[FONT=Arial]gpg: out of memory while allocating 8192 bytes[/FONT][FONT=Times New Roman] 

[/FONT]
[FONT=Times New Roman]Truss output from a server where its WORKING :

[FONT=Arial]$ t-self --yes --encrypt-files sample3 > truss.out <[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]execve("/usr/bin/gpg", 0x2FF22C54, 0x2000FB38) argc: 7[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]execve("/etc/gpg", 0x2FF22C54, 0x2000FB38) argc: 7[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]execve("/usr/sbin/gpg", 0x2FF22C54, 0x2000FB38) argc: 7[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]execve("/usr/ucb/gpg", 0x2FF22C54, 0x2000FB38) argc: 7[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]execve("/home/adwodadm/bin/gpg", 0x2FF22C54, 0x2000FB38) argc: 7[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]execve("/usr/bin/X11/gpg", 0x2FF22C54, 0x2000FB38) argc: 7[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]execve("/sbin/gpg", 0x2FF22C54, 0x2000FB38) argc: 7[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]execve("./gpg", 0x2FF22C54, 0x2000FB38) argc: 7[/FONT][FONT=Times New Roman] 
[/FONT][FONT=Arial]_exit(127)[/FONT][IMG]http://linux.unix.com/images/misc/progress.gif[/IMG]
[/FONT]

---

### Post by sradithya on 2013-01-22
The gpg process is not running as a daemon on the server. Its a stand alone software which is invoked by the batch scripts (shell scripts) at scheduled times run by admin ids.
 
There is no centralized trustdb for all the id's. There are individual trustdbs for all the admin ids in their own home directories. The trustdbs are not expected to be corrupted and are in tact.
 
Please find the encryption outputs run with debug options on the server where it is working and where it isnt.
 
Debug output - Server where gpg is working:
 
```
$ /opt/TWWfsw/gnupg12/bin/gpg --debug-all --encrypt-file simple1
gpg: NOTE: no default option file `/home/a510373/.gnupg/options'
You did not specify a user ID. (you may use "-r")
Enter the user ID. End with an empty line: sradithya
Added 1024g/212DCF43 2013-01-18 "sradithya (Hi) <[EMAIL="Aditya.Sr@abc.com"]Aditya.Sr@abc.com[/EMAIL]>"
Enter the user ID. End with an empty line:
File `simple1.gpg' exists. Overwrite (y/N)? y
$ ls -lrt
-rwxrwxrwx 1 a510373 adwsup 6 Jan 20 13:41 simple1
-rw-r--r-- 1 a510373 adwsup 347 Jan 20 19:45 simple1.gpg
```
 
Debug output - Server where gpg is NOT working:
 
```
/home/a510373 >/opt/TWWfsw/gnupg12/bin/gpg --debug-all --encrypt-file simple1
gpg: NOTE: no default option file `/home/a510373/.gnupg/options'
You did not specify a user ID. (you may use "-r")
Enter the user ID. End with an empty line: sradithya
gpg: DBG: fd_cache_open (/home/a510373/.gnupg/pubring.gpg) not cached
gpg: DBG: iobuf-1.0: open `/home/a510373/.gnupg/pubring.gpg' fd=4
gpg: DBG: iobuf-1.0: underflow: req=8192
gpg: DBG: iobuf-1.0: underflow: got=1819 rc=0
gpg: DBG: parse_packet(iob=1): type=6 length=418 (search.keyring.c.963)
gpg: DBG: mpi_alloc(1024)
gpg: DBG: mpi_alloc_limb_space(1024)
gpg: DBG: mpi_alloc(160)
gpg: DBG: mpi_alloc_limb_space(160)
gpg: DBG: mpi_alloc(1024)
gpg: DBG: mpi_alloc_limb_space(1024)
gpg: DBG: mpi_alloc(1024)
gpg: DBG: mpi_alloc_limb_space(1024)
gpg: DBG: free_packet() type=6
gpg: DBG: mpi_free
gpg: DBG: dummy m_size called
gpg: DBG: mpi_free_limb_space of size 0
gpg: DBG: mpi_free
gpg: DBG: dummy m_size called
gpg: DBG: mpi_free_limb_space of size 0
gpg: DBG: mpi_free
gpg: DBG: dummy m_size called
gpg: DBG: mpi_free_limb_space of size 0
gpg: DBG: mpi_free
gpg: DBG: dummy m_size called
gpg: DBG: mpi_free_limb_space of size 0
gpg: DBG: parse_packet(iob=1): type=13 length=37 (search.keyring.c.963)
gpg: DBG: fd_cache_open (/home/a510373/.gnupg/pubring.gpg) not cached
gpg: DBG: iobuf-2.0: open `/home/a510373/.gnupg/pubring.gpg' fd=5
gpg: DBG: iobuf-2.0: underflow: req=8192
gpg: DBG: iobuf-2.0: underflow: got=1819 rc=0
gpg: DBG: parse_packet(iob=2): type=6 length=418 (search.keyring.c.963)
gpg: DBG: mpi_alloc(1024)
gpg: DBG: mpi_alloc_limb_space(1024)
gpg: DBG: mpi_alloc(160)
gpg: DBG: mpi_alloc_limb_space(160)
gpg: DBG: mpi_alloc(1024)
gpg: DBG: mpi_alloc_limb_space(1024)
gpg: DBG: mpi_alloc(1024)
gpg: DBG: mpi_alloc_limb_space(1024)
gpg: DBG: free_packet() type=6
gpg: DBG: mpi_free
gpg: DBG: dummy m_size called
gpg: DBG: mpi_free_limb_space of size 0
gpg: DBG: mpi_free
gpg: DBG: dummy m_size called
gpg: DBG: mpi_free_limb_space of size 0
gpg: DBG: mpi_free
gpg: DBG: dummy m_size called
gpg: DBG: mpi_free_limb_space of size 0
gpg: DBG: mpi_free
gpg: DBG: dummy m_size called
gpg: DBG: mpi_free_limb_space of size 0
gpg: DBG: fd_cache_open (/home/a510373/.gnupg/pubring.gpg) not cached
gpg: DBG: iobuf-3.0: open `/home/a510373/.gnupg/pubring.gpg' fd=6
gpg: DBG: iobuf-3.0: underflow: req=8192
gpg: DBG: iobuf-3.0: underflow: got=1819 rc=0
gpg: DBG: parse_packet(iob=3): type=6 length=418 (parse.keyring.c.382)
gpg: DBG: mpi_alloc(1024)
gpg: DBG: mpi_alloc_limb_space(1024)
gpg: DBG: mpi_alloc(160)
gpg: DBG: mpi_alloc_limb_space(160)
gpg: DBG: mpi_alloc(1024)
gpg: DBG: mpi_alloc_limb_space(1024)
gpg: DBG: mpi_alloc(1024)
gpg: DBG: mpi_alloc_limb_space(1024)
gpg: DBG: parse_packet(iob=3): type=13 length=37 (parse.keyring.c.382)
gpg: DBG: parse_packet(iob=3): type=2 length=94 (parse.keyring.c.382)
gpg: DBG: mpi_alloc(160)
gpg: DBG: mpi_alloc_limb_space(160)
gpg: DBG: mpi_alloc(160)
gpg: DBG: mpi_alloc_limb_space(160)
gpg: DBG: parse_packet(iob=3): type=12 length=2 (parse.keyring.c.382)
gpg: DBG: parse_packet(iob=3): type=14 length=269 (parse.keyring.c.382)
gpg: DBG: mpi_alloc(1024)
gpg: DBG: mpi_alloc_limb_space(1024)
gpg: DBG: mpi_alloc(32)
gpg: DBG: mpi_alloc_limb_space(32)
gpg: DBG: mpi_alloc(1024)
gpg: DBG: mpi_alloc_limb_space(1024)
gpg: DBG: parse_packet(iob=3): type=2 length=73 (parse.keyring.c.382)
gpg: DBG: mpi_alloc(160)
gpg: DBG: mpi_alloc_limb_space(160)
gpg: DBG: mpi_alloc(160)
gpg: DBG: mpi_alloc_limb_space(160)
gpg: DBG: parse_packet(iob=3): type=12 length=2 (parse.keyring.c.382)
gpg: DBG: parse_packet(iob=3): type=6 length=418 (parse.keyring.c.382)
gpg: DBG: mpi_alloc(1024)
gpg: DBG: mpi_alloc_limb_space(1024)
gpg: DBG: mpi_alloc(160)
gpg: DBG: mpi_alloc_limb_space(160)
gpg: DBG: mpi_alloc(1024)
gpg: DBG: mpi_alloc_limb_space(1024)
gpg: DBG: mpi_alloc(1024)
gpg: DBG: mpi_alloc_limb_space(1024)
gpg: DBG: free_packet() type=6
gpg: DBG: mpi_free
gpg: DBG: dummy m_size called
gpg: DBG: mpi_free_limb_space of size 0
gpg: DBG: mpi_free
gpg: DBG: dummy m_size called
gpg: DBG: mpi_free_limb_space of size 0
gpg: DBG: mpi_free
gpg: DBG: dummy m_size called
gpg: DBG: mpi_free_limb_space of size 0
gpg: DBG: mpi_free
gpg: DBG: dummy m_size called
gpg: DBG: mpi_free_limb_space of size 0
gpg: DBG: iobuf-3.0: close `file_filter(fd)'
gpg: DBG: /home/a510373/.gnupg/pubring.gpg: close fd 6
gpg: DBG: fd_cache_close (/home/a510373/.gnupg/pubring.gpg) new slot created
gpg: DBG: build_packet() type=6
gpg: out of memory while allocating 8192 bytes
```
 
Please find the truss outputs run on gpg on the server where it is working and where it isn't working.
 
Truss output - Server where gpg is working:
 
```
$ t-self --yes --encrypt-files sample3 > truss.out < 
execve("/usr/bin/gpg", 0x2FF22C54, 0x2000FB38) argc: 7 
execve("/etc/gpg", 0x2FF22C54, 0x2000FB38) argc: 7 
execve("/usr/sbin/gpg", 0x2FF22C54, 0x2000FB38) argc: 7 
execve("/usr/ucb/gpg", 0x2FF22C54, 0x2000FB38) argc: 7 
execve("/home/adwodadm/bin/gpg", 0x2FF22C54, 0x2000FB38) argc: 7 
execve("/usr/bin/X11/gpg", 0x2FF22C54, 0x2000FB38) argc: 7 
execve("/sbin/gpg", 0x2FF22C54, 0x2000FB38) argc: 7 
execve("./gpg", 0x2FF22C54, 0x2000FB38) argc: 7 
_exit(127) 
```
 
Truss output - Server where gpg is NOT working:
 
```
home> truss /opt/TWWfsw/bin/gpg --verbose --default-recipient-self --yes --encrypt-files sample2 > truss.out 
execve("/usr/bin/gpg", 0x2FF2253C, 0x2000FB38) argc: 7 
execve("/etc/gpg", 0x2FF2253C, 0x2000FB38) argc: 7 
execve("/usr/sbin/gpg", 0x2FF2253C, 0x2000FB38) argc: 7 
execve("/usr/ucb/gpg", 0x2FF2253C, 0x2000FB38) argc: 7 
execve("/home/adwodadm/bin/gpg", 0x2FF2253C, 0x2000FB38) argc: 7 
execve("/usr/bin/X11/gpg", 0x2FF2253C, 0x2000FB38) argc: 7 
execve("/sbin/gpg", 0x2FF2253C, 0x2000FB38) argc: 7 
execve("./gpg", 0x2FF2253C, 0x2000FB38) argc: 7 
execve("/datastage/adwprod_753_app/Ascential/DataStage/DSEngine/bin/gpg", 0x2FF2253C, 0x2000FB38) argc: 7 
execve("./gpg", 0x2FF2253C, 0x2000FB38) argc: 7 
truss: 0915-007 Lost control of process. 
gpg: using secondary key D8C00BBB instead of primary key 97DBC284 
gpg: reading from `sample2' 
gpg: writing to `sample2.gpg' 
gpg: ELG-E/AES256 encrypted for: "D8C00BBB test01 (test ods) <[EMAIL="abakcie@abc.com"]abakcie@abc.com[/EMAIL]>" 
gpg: out of memory while allocating 8192 bytes
```

---

### Post by mike acker on 2013-01-22
you should take this issue to the GPG Support area:

[gnupg-users@gnupg.org]("http://ubuntuforums.org/gnupg-users@gnupg.org")

the debug output does not identify the problem in a manner that will allow you to correct it.

someday programmers will learn to write diagnostic messages that allow users to correct problems . until then we have to pay for Stout.

~~
in the debug output you notice
```

gpg: DBG: fd_cache_open (/home/a510373/.gnupg/pubring.gpg) not cached

```you should know that Linux normally "caches" (reads into memory ) files that it is working with -- when there is available RAM

"not cached" then may mean "not found "  . remember that in this kind of problem we have to question what each message actually means. misleading messages can put you up the wrong tree for days...

next notice that it is looking in 
```

/home/a510373/.gnupg/pubring.gpg

```/home/ -- represents the current user...

the .gnupg --- represents an alias or shortcut -- that should take you out of the user path to the location of the keyring

TRACE it as follows:
```

cd /
cd mike
mike@acker:~$ cd .gnupg
mike@acker:~/.gnupg$ ls
gpg.conf  pubring.gpg  pubring.gpg~  random_seed  secring.gpg  trustdb.gpg
mike@acker:~/.gnupg$ pwd
/home/mike/.gnupg
mike@acker:~/.gnupg$ 

```this is to verify that you can get to the keyring...
after that: do you have permission to use the keyring? that will be controlled by RACF and "permission denied" may be reported as "not found" . generally for security reasons we do not tell you that you have a security violation.

access rights on the keyering show as RW for the OWNER . this is an area to check . in Linux you congtrol it with chmod, chowner, chgrp but your AIX machine likely has RACF as well

a function such as --LISTKEYS might issue an open for the keyring in READ mode... and execute OK but normal use of GPG will use RW mode as you may be updating the keys.  we don't know what it uses when you direct it to --encrypt a file . but this could explain why the process fails doing --encrypt and works with --list-keys 

it seems clear that your server restore did not put something back right

get with the support group they should be able to tell you what to check .

---

### Post by sradithya on 2013-01-22
Thanks for your inputs. I wanted to consolidate some more observations below :
 
WRITE/EDIT OPTIONS ARE ONLY FAILING :
 
Trying to do an encryption :
 
```
//home> truss /opt/TWWfsw/bin/gpg --verbose --default-recipient-self --yes --encrypt-files sample2 > truss.out 
execve("/usr/bin/gpg", 0x2FF2253C, 0x2000FB38)   argc: 7 
execve("/etc/gpg", 0x2FF2253C, 0x2000FB38)       argc: 7 
execve("/usr/sbin/gpg", 0x2FF2253C, 0x2000FB38)  argc: 7 
execve("/usr/ucb/gpg", 0x2FF2253C, 0x2000FB38)   argc: 7 
execve("/home/bin/gpg", 0x2FF2253C, 0x2000FB38)  argc: 7 
execve("/usr/bin/X11/gpg", 0x2FF2253C, 0x2000FB38)  argc: 7 
execve("/sbin/gpg", 0x2FF2253C, 0x2000FB38)      argc: 7 
execve("./gpg", 0x2FF2253C, 0x2000FB38)          argc: 7
execve("/datastage/aprod_753_app/Ascential/DataStage/DSEngine/bin/gpg", 0x2FF2253C, 0x2000FB38)  argc: 7 
execve("./gpg", 0x2FF2253C, 0x2000FB38)          argc: 7 
truss: 0915-007 Lost control of process. 
gpg: using secondary key D8C00BBB instead of primary key 97RGV098 
gpg: reading from `sample2' 
gpg: writing to `sample2.gpg' 
gpg: ELG-E/AES256 encrypted for: "D8CDFRRG test01 (test ods) <[EMAIL="adserr@abc.com"]adserr@abc.com[/EMAIL]>" 
gpg: out of  memory while allocating 8192 bytes
```
 
Please note that it is failing while trying to read the data and write it in the encrypted format.
 
Or when we tried editing the keys :
 
```
$ /opt/TWWfsw/bin/gpg --edit-key Joseph Johnson
gpg (GnuPG) 1.2.3; Copyright (C) 2003 Free Software Foundation, Inc.
This program comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details.
Secret key is available.
gpg: checking the trustdb
gpg: out of  memory while allocating 8192 bytes
$
```
 
READ OPERATIONS ARE SUCCEEDING : 
 
```
/home/a510373 >/opt/TWWfsw/bin/gpg --list-key
/home/a510373/.gnupg/pubring.gpg
--------------------------------
pub  1024D/9FA4A9F0 2013-01-18 sradithya (Hi) <[EMAIL="Aditya.Sr@abc.com"]Aditya.Sr@abc.com[/EMAIL]>
sub  1024g/8CF038A9 2013-01-18
pub  1024D/45834B11 2013-01-18 sraditya (Hi) <[EMAIL="sraditya@gmail.com"]sraditya@gmail.com[/EMAIL]>
sub  1024g/3A935DA1 2013-01-18
/home/a510373 >
/home/a510373 >/opt/TWWfsw/bin/gpg --version
gpg (GnuPG) 1.2.3
Copyright (C) 2003 Free Software Foundation, Inc.
This program comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details.
Home: ~/.gnupg
Supported algorithms:
Pubkey: RSA, RSA-E, RSA-S, ELG-E, DSA, ELG
Cipher: 3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH
Hash: MD5, SHA1, RIPEMD160, TIGER192, SHA256
Compression: Uncompressed, ZIP, ZLIB
/home/a510373 >
```

Hence, the gpg is trying to use some memory for the write/edits that is currently failing. If we would be able to figure out this memory where it is temporarily trying to store data, we would be able to crack the issue.

---

### Post by mike acker on 2013-01-22
> **sradithya said:**
> Thanks for your inputs. I wanted to consolidate some more observations below :
 
WRITE/EDIT OPTIONS ARE ONLY FAILING :
 {snip}

Hence, the gpg is trying to use some memory for the write/edits that is currently failing. If we would be able to figure out this memory where it is temporarily trying to store data, we would be able to crack the issue.

that you should find in the RACF or server log
 have you posted your trouble logs to the support group?

GnuPG is supportted on a mail list:
[gnupg-users@gnupg.org]("http://ubuntuforums.org/gnupg-users@gnupg.org")

on this open-source software support is contributed by volunteers . the better you are at presenting your problem analysis the better results you will get .

one thing I do want you to do though: 

issue a whereis and find out where the gpg program is kept on your system :
```

$ whereis gpg
gpg: /usr/bin/gpg /usr/bin/X11/gpg

```

after you have that go to that directory:
```

on Ubuntu :
$ cd /usr/bin/X11

$ pwd
/usr/bin/X11


```

once you are there ll gpg as follows:
```

$ ll gpg
-rwxr-xr-x 1 root root 991680 Jan  8 15:28 gpg*

```

note the program is 991680 bytes dated Jan8 15:28

I apply maintenance on my system regularly so the Jan8 date most likely resulted from a recent update.

check your bad server with you good one make sure gpg is the same on both .

---

### Post by mike acker on 2013-01-24
sradithya pls let us know what you final determination is on this
thanks

---

### Post by Eglefino on 2013-01-24
> **mike acker said:**
> 
~~~~~
-- what's your natural language ??  your profile doesn't make a note...
-- what version of Ubuntu are you on? 12.04 or 12.04 LTS . this should be in your profile
~~~~~

You know the same as other newbie I'm not allowed to write my profile, I wrote a message to the top, in the hope they can flexible those rules to disabled and/or bedridden persons, otherwise it's discrimination (the rules are made for several healthy persons who want fast information and never come back again). I cannot write in every message a part of my profile and/or for what OS, for that I  have no energy for that. I'm a 58-year Dutchman and because of my syndromes I bump in every forum my head because I don't get a equal treatment, most people don't know how it is if you are in my situation without help. In the Netherlands it's sometimes bad and sometimes good. To have 24/7 pain can make a 'normal' person (if they exist) a horrible. We ill persons are dependent on others round our home/family.... if the family is lazy or is understandable you have to fight for your own rights 
I work wit the Long term version Precise and 'had' 32-year experience with soft/hardware from the past most with Windows. I came from Atari/Commodore64-period. So now is my energy empty... bluh... you have to wait until my body can more.
> **mike acker said:**
> 
first off, what are you trying to do ??  GPG comes with your Ubuntu system and the agent should be active when you start the system

try the basic: From TERMINAL :

I try to get the Code of Conduct of Ubuntu from Launchpad.net see my profile I have no OpenPGP code, I did all you wrote before, than I get a gpg but no OpenPgP!! I have enigmale, Fire... sorry sometimes I forget the names no energy, stop

> **mike acker said:**
> 

if you do then you GPG is ready for use

most likely you want to use it with Thunderbird. Thunderbird also comes pre-installed on your 12.04 system and in  spite of what Kim Kommando sez it's a terriffic e/mail client . to use PGP with Thunderbird active the ENIGMAIL plug-in and then generate your key-pair .  remember to always generate a REVOKE key when you create a new key

there is also an e/mail list : [EMAIL="enigmail-users@enigmail.net"]enigmail-users@enigmail.net[/EMAIL]

you should do most of your GPG work using the Key Management menu in Thunderbird .

---

