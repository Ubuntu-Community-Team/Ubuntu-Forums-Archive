---
title: "[SOLVED] Understanding GnuPG"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2008-01-11
Ok, I have not fully grasped the concept of GPG, but I do understand encryptions, that's why I am really trying to figure this out. So basically, look at me with a knowledge level of zero, and please help me to figure this out.

So, I have made a key, I got that far, I made a fingerprint, and was going to submit it to launchpad to verify my OpenPGP key or whatever, it sent me an email and said I had to decrypt it to get the link out of it.

I have yet to figure out HOW to decrypt it. I have FireGPG for Firefox, and it couldn't decrypt it, it wouldn't even let me enter my pass phrase.

SO I am somewhat confused about all of this.

Another thing, what public key do I give out to someone, for them to encrypt messages to me with? The actual key or the Armored key? All of this is very confusing to me, and I had done alot of searching on Google last night for hours and couldn't find any basic guides to understand it all.

So if anyone can shed any light on this, I'd be very happy :)

Dr Small

---

### Post by drs305 on 2008-01-11
I don't use fireGPG but the following link talks you through the general concepts of gpg and how to set it up. There is a lot of terminal output but the explanations at each step are written so a layman can understand what is going on.
[http://aplawrence.com/Basics/gpg.html](http://aplawrence.com/Basics/gpg.html)

Another is
[http://www.madboa.com/geek/gpg-quickstart/](http://www.madboa.com/geek/gpg-quickstart/)

---

### Post by Dr Small on 2008-01-11
Thanks for the help, and I have read those links already. I can encrypt my own text with my public key, and then decrypt it with my private key, but when I sent my fingerprint to launchpad to verify my key, they said that I needed to decrypt it with my private key.

So far, I have yet to be able to decrypt it. Here is what they sent me, but nothing I have tried so far will decrypt it:
> -----BEGIN PGP MESSAGE-----
Version: GnuPG v1.4.2.2 (GNU/Linux)

hQIOAzll2+N+8y3QEAgAg3cPRkkAMKDhO+qHRUl7BPZeQmf8xFL3w8rtJ6iJK4d+
ZBJmrF1peWawowJvxhf/iA8Pa3vrVkgPHdGUuECabgu6MysJuA1jQ9u2FIgEZVYl
3t04Yze7LkS5DnZ7g3OIzeLw2g55RAAK/5Q12AQJ/ww8eozpnmvUz+E2Es6Uggwy
D1TGGKBBFx9fJzQiVMCprR1YfitAr3Lv8jKJACy58IY7EvMsOmac+x3asHQpR+Bz
DFPC2nIzylDajZdLh2tQkF1lSjj6Y/67Z8rpjh6KdJkp8B4aqCUaueE2gKISX3RN
pQ6qfYt7VJVZSuJ+KFb3b0b3M+yjRnq25nCocLos7Af9HhuGFNPMw944o7M3iDyY
xtq3EAPRhB+ptUC07CFkmuaKKw2bUIIkpkBKU8vrPf0J+iZ6rBazwwcNS98A2MTw
rhjY9LJJo2k92Ire1k1AWzE09l0zf/QhPoKxGlwMJRqVxDWcDFowtPbUK9BpjdI/
2jDvbFxZV1oBHlwCTCUKCHD364BgvWhat the!?ZmEU+3ZZPyduUovPHTy792MhxxWTABcj
1YfDsBm1E6UGz4gxVF5DauUL4TT/0K6fZbCUz67iyjpqwMH1g+nUQY9xMLdV9NQu
KCDTnNzBH6q+DegvVm68402JlyZhLEwunhRWDPr8TWF6XV3O4gHmUgTkj4tyQKZj
q9LAtQHvkv8cJMt/UQ5euJNnaZPWHMNFUsO3E6pz0dyVoZ0CeOiBo0TyzxOUC5lC
X+AVl9tOFp5bEuR4cos6bP/2oTpCvkg7mC9gmf9XmlLYS0XWj9MmQMV/kf1FooF1
t2mOWDP0nyLAJRkpZ4CdC1dl4/YhlJpDEbVnpANLVX4zLNACSmCZC0yI2I+i4+Zc
gW/UjxuvgkeV5cj0sWt5dhcgiP3LnCiAbCwiXaheUr7p9ezn4jgNDmhBJQ5Euh5A
q5uFvqvKdt5JVwrWVMSbRKqt8hksq3p+Zk44+eUNb0xLUVpnKVTeW9BxVq6F81zT
r05kcpRt1A3wlzrFp44oBZMclC1KgjCe0C0/qiJB1zpPMsqUDmHcx4oFTKwBochq
w6Rw/wN+5CXcv3cTXVBGdIyYP8CB73GYqUH4cTzNVYtv0wj3+HElR9kcTwptBBjV
igS0EHA+TFUy/xiv4+MDvSl9khzI+l5DjQb4IvLFlFnm2azgkPh1ePY=
=7rh9
-----END PGP MESSAGE-----


Everything I try, says No data.
Also, if I want someone to encrypt a message to me, do I give them my armored key, or "26FD8AF9" ?

---

### Post by FuturePilot on 2008-01-11
Are you using an email client such as Thunderbird or Evolution? I know for Thunderbird there's an extension called Enigmail that will decrypt your emails. Evolution can do it by without any extras.
Sorry if this isn't the case. ;)

---

### Post by Dr Small on 2008-01-11
No, just plain ole webmail.
But shouldn't I be able to decrypt that message with my private key somehow, anyway?

---

### Post by drs305 on 2008-01-11
> **Dr Small said:**
> 
Another thing, what public key do I give out to someone, for them to encrypt messages to me with? The actual key or the Armored key?
Dr Small

From the second link I mentioned above:

***
Generate an ASCII public version of your private key.
```
gpg --armor --output pubkey.txt --export 'Your Name'
```
You can freely distribute this file by sending it to friends, posting it on your web site, or whatever.
***

So the file you send to your friends would be the one generated using the above command. The link then continues:
***
If someone sends you an encrypted file, the file has typically been encrypted using your public key.
***

---

### Post by Niniel on 2008-01-11
You give people your public key so that they can encrypt messages to you that you then will be able to decrypt (with your private key). Conversely, you'll need their public key to send them encrypted messages that they can decrypt. 

Read this for an [introduction to PGP]("http://www.pgpi.org/doc/pgpintro/").

This here explains it nicely:

> Public key cryptography is an asymmetric scheme that uses a pair of keys for encryption: a public key, which encrypts data, and a corresponding private, or secret key for decryption. Youpublishyour public keytotheworldwhile keeping your private key secret. Anyone with a copy of your public key can then encrypt information that only you can read. Even people you have never met.

---

### Post by Dr Small on 2008-01-11
Ok thanks for that. I think I am beginning to understand it partway.
But I'm still hung up as to why I can't decrypt the message sent from launchpad.

At the beginning of their email, they state:
> Hello,

This message contains the instructions for confirming registration of an
OpenPGP key for use in Launchpad.  The confirmation instructions have been
encrypted with the OpenPGP key you have attempted to register.  If you cannot
read the unencrypted instructions below, it may be because your mail reader
does not support automatic decryption of "ASCII armored" encrypted text.

They keep refering to OpenPGP, and I am using GnuPG and gpg. Maybe this is a problem??

Dr Small

---

### Post by FuturePilot on 2008-01-11
I decided to try Firegpg and I was getting the same No Data error. But I figured it out. You have to highlight the entire thing from
-----BEGIN PGP MESSAGE-----
to
-----END PGP MESSAGE-----
and then Decrypt it. So just try highlighting the whole thing in your other post.

---

### Post by seventhc on 2008-01-11
This may be a bit off topic regarding this thread, but just one question about pgp. I don't understand the point of encryption when anyone with the public key can decrypt it. The public key servers are easy enough to search, so I guess what I am saying is that I don't really understand where the security is.
I can understand it for digital signatures but not for encryption. Can anyone explain this to me please?
Sorry if I should have started a new thread, if it's necessary I can do, but I figured to ask here since I'm not opening with a new problem, just a question. Thanks for any input. :)

---

### Post by Dr Small on 2008-01-11
> **FuturePilot said:**
> I decided to try Firegpg and I was getting the same No Data error. But I figured it out. You have to highlight the entire thing from
-----BEGIN PGP MESSAGE-----
to
-----END PGP MESSAGE-----
and then Decrypt it. So just try highlighting the whole thing in your other post.
Hmm. There must be something wrong on my end then... Because FireGPG comes up and says: "Decryption failed. Unknown Error"... It don't make no sense.

---

### Post by Niniel on 2008-01-11
You don't _de_crypt with the public key, you just _en_crypt. So anybody can send you encrypted messages. But only the owner of the private key that's corresponding to the public key that was used for encryption - aka you - can decrypt the message.

---

### Post by Dr Small on 2008-01-11
> **seventhc said:**
> This may be a bit off topic regarding this thread, but just one question about pgp. I don't understand the point of encryption when anyone with the public key can decrypt it. The public key servers are easy enough to search, so I guess what I am saying is that I don't really understand where the security is.
I can understand it for digital signatures but not for encryption. Can anyone explain this to me please?
Sorry if I should have started a new thread, if it's necessary I can do, but I figured to ask here since I'm not opening with a new problem, just a question. Thanks for any input. :)
Ok, Picture it like this.

Joe has a public and private key.
Bob has a public and private key.

Joe sends a message to Bob, by encrypting the message with Bob's private key.
Bob can decrypt the message, because it has been encrypted with his public key and can only be decrypted with his private key.

If anyone intercepts the message encrypted with Bob's public key, they can not decrypt it because they do not hold Bob's private key. Not even Joe can decrypt the message that he just encrypted to Bob.

That's where the security comes in.
But I just don't get (for my problem), how I can't decrypt the message from launchpad when they encrypted it with my public key.

Dr Small

---

### Post by seventhc on 2008-01-11
> **Dr Small said:**
> Ok, Picture it like this.

Joe has a public and private key.
Bob has a public and private key.

Joe sends a message to Bob, by encrypting the message with Bob's private key.
Bob can decrypt the message, because it has been encrypted with his public key and can only be decrypted with his private key.

If anyone intercepts the message encrypted with Bob's public key, they can not decrypt it because they do not hold Bob's private key. Not even Joe can decrypt the message that he just encrypted to Bob.

That's where the security comes in.
But I just don't get (for my problem), how I can't decrypt the message from launchpad when they encrypted it with my public key.

Dr Small
Thanks for the explanation, makes sense now.
About your problem, did you try downloading the encrypted message to your computer?? Maybe once you dl it you'll be able to decrypt it.
Are you using seahorse? If so, I think once you have it on your computer you can just right click on it and select decrypt.
Not sure if it will work or not, but i think it's something to try. :)

---

### Post by Dr Small on 2008-01-11
Yeah, I've tried all of those methods. None have worked. I tried from FireGPG, downloaded it, tried decrypting it, tried from the command line. Oh, here is the error I get from the command line:

```
drsmall@darkghost:~$ gpg --decrypt launchpad.gpg 
gpg: invalid radix64 character 21 skipped
gpg: invalid radix64 character 3F skipped
gpg: CRC error; 2BA7FA - EEB87D

```

By the way, would anyone mind sending me an encrypted message for a test, to see if I can actually decrypt it ?
My public key is here:
[http://php.8ez.com/drsmall/public.key](http://php.8ez.com/drsmall/public.key)

Dr Small

---

### Post by seventhc on 2008-01-11
If I can figure out how to do it I'll send you an email, but I've never encrypted a message with someones public key before. btw, whats your email address?

---

### Post by Dr Small on 2008-01-11
> **seventhc said:**
> If I can figure out how to do it I'll send you an email, but I've never encrypted a message with someones public key before. btw, whats your email address?
drsmall [AT] hackermail [DOT] com

I find that encrypting and decrypting work pretty good if you use FireGPG. ;)

---

### Post by seventhc on 2008-01-11
I'm using mutt :D

---

### Post by Niniel on 2008-01-11
Have you tried using a plug-in for your mail program? I used to have Eudora with the PGP plugin, that was very painless to use and not difficult to set up. Haven't used any encryption with Thunderbird yet, but there's a plugin for that as well, I believe it's called [Enigmail]("http://enigmail.mozdev.org/home/index.php").

---

### Post by seventhc on 2008-01-11
I installed firePGP, now how do I get your public key into it so i can encrypt the email with your key?
When I go to encrypt it, it wants to use my key.

---

### Post by seventhc on 2008-01-11
> **Niniel said:**
> Have you tried using a plug-in for your mail program? I used to have Eudora with the PGP plugin, that was very painless to use and not difficult to set up. Haven't used any encryption with Thunderbird yet, but there's a plugin for that as well, I believe it's called [Enigmail]("http://enigmail.mozdev.org/home/index.php").
enigmail won't work with mutt will it??
The only thing I know how to do is to sign mail since I don't know anyone who uses encryption. My muttrc is set up for it, but I was never sure about importing the public keys. I know how to encrypt to myself though lol

---

### Post by Dr Small on 2008-01-11
```
gpg --import public.key
```
Or, if you have seahorse or GPA, just click import.

Dr Small

---

### Post by seventhc on 2008-01-11
When I go to import it, it is looking for my key...or so I think.
I thought i could get it from your email addi...like search the key servers then bring it in to use.
sorry for being such a newb about this.

---

### Post by Dr Small on 2008-01-11
If you download the key first, and then run the import command, it will import my key.

```
wget http://php.8ez.com/drsmall/public.key
gpg --import public.key
```

Or, if you want to do it graphically, just install seahorse and click the import button.
```
sudo apt-get install seahorse
```

Dr Small

---

### Post by seventhc on 2008-01-11
sent...i have seahorse already, but I do think it is easier doing the import from the terminal. thanks for teaching me too :)

---

### Post by Dr Small on 2008-01-11
Ok then. I MUST be doing something wrong. I am basically getting the same error from FireGPG and the command line:
```
drsmall@darkghost:~$ gpg -d j0hn 
gpg: invalid radix64 character 21 skipped
gpg: invalid radix64 character 3F skipped
gpg: CRC error; C0E592 - 13FFCB
gpg: encrypted_mdc packet with unknown version 255

```

Am I missing something? Or some package?

---

### Post by seventhc on 2008-01-11
are you synced up with the key servers?? not sure if it matters or not

---

### Post by Dr Small on 2008-01-11
I have no idea. Probably not, but it's worth a shot. How would I go about doing that?
It really seems odd, because I can decrypt my own messages that I encrypt with my Public key, but can't decrypt anything I receive from others...

Dr Small

---

### Post by seventhc on 2008-01-11
If you have seahorse you click on remote then 'sync and publish keys'...
or from terminal

gpg --keyserver pgp.mit.edu --send-key 'key id'

---

### Post by Dr Small on 2008-01-11
Same problem, even after I synced the key with the servers... Hrm. This is disappointing.

Dr Small

---

### Post by seventhc on 2008-01-11
do you get output if you type
gpg -K
at the terminal?

---

### Post by Dr Small on 2008-01-11
> **seventhc said:**
> do you get output if you type
gpg -K
at the terminal?
Yup.
It tells me my public key, name, email and private key.

---

### Post by seventhc on 2008-01-11
I think we need a gpg guru
:confused::confused::confused:

---

### Post by Dr Small on 2008-01-11
I completely agree. :| :(

---

### Post by seventhc on 2008-01-11
check your mail :D check the options in fireGPG and put checks in both boxes under gpgAUTH.

---

### Post by Xavieran on 2008-01-11
Have another go...I don't think you need to sync with the servers if you are using a key you created yourself...I'll attach a file encrypted for you...I would use seahorse...it has nautilus plugins that make it really easy to Decrypt and Re Encrypt ...:)

P.S...
I had to change the file extension or Ubuntu Forums wouldn't have accepted it...just change it back to .tar.pgp once you have it...:)

---

### Post by Xavieran on 2008-01-11
Have another go...I don't think you need to sync with the servers if you are using a key you created yourself...I'll attach a file encrypted for you...I would use seahorse...it has nautilus plugins that make it really easy to Decrypt and Re Encrypt ...:)

P.S...
I had to change the file extension or Ubuntu Forums wouldn't have accepted it...just change add .pgp once you have it...:)


Sorry...I didn't realise I duoble posted :(

---

### Post by Dr Small on 2008-01-11
Ok, that seemed to have worked, and you encrypted it with my public key.
So, why can't I decrypt stuff that launchpad or seventhc send me that is encrypted with my public key ?

Dr Small

---

### Post by Xavieran on 2008-01-11
What procedure did you follow to decrypt that file?

Maybe just try to repeat it with the messages launchpad sends you...Save to disc, rename with a .pgp and decrypt?

---

### Post by Dr Small on 2008-01-11
I asked a question at launchpad:
[https://answers.launchpad.net/ubuntu/+question/21980](https://answers.launchpad.net/ubuntu/+question/21980)

And it explains it pretty well.
But no matter how I try to decrypt it, I always get this error:
```
gpg: invalid radix64 character 21 skipped
gpg: invalid radix64 character 3F skipped
gpg: CRC error; 2BA7FA - EEB87D

```

Dr Small

---

### Post by Xavieran on 2008-01-11
Are you _absolutely sure_ you have the correct key?
If they are using a key that is different to the one you made ...

Heres some info...
[QUOTE=Launchpad]Launchpad could not import your OpenPGP key.

    * Did you enter your complete fingerprint correctly? A fingerprint is a long sequence of numbers and letters. You should use the output produced by the command:

          gpg --fingerprint 
[B][U]
    * Have you published your key to a public key server? You can do that by by entering in a terminal:

          gpg --keyserver keyserver.ubuntu.com --send-keys 

    * Has your key been automatically mirrored to the Ubuntu key server? Keys sometimes take up to an hour to be synchronized between servers. You can check if it has by querying the Ubuntu key server directly. If it hasn't, you can publish directly to our server by entering in a terminal:

          gpg --keyserver keyserver.ubuntu.com --send-keys [/U][/B]

[/QUOTE]

---

### Post by Dr Small on 2008-01-11
I'm trying to think of how I would have gotten a different key ?!
Launchpad required me to upload it to their keyserver, so I did that some months back, and couldn't figure it out, and then they required you to enter the fingerprint, so i just tried again.

It sent out the email, and from this day (since yesterday) i have yet to decrypt it...
My fingerprint should be the following (from what gpg outputs)
```
21E3 4797 0865 F28F F424  192E BC98 50A9 26FD 8AF9
```

And I sent this one to launchpad:
```
21E347970865F28FF424192EBC9850A926FD8AF9
```

So I am as completely confused (if not worse) as everyone else.

Dr Small

---

### Post by seventhc on 2008-01-11
I would think if you can decrypt the message from Xavieran then there isn't anything wrong with your key...but figuring out why you can decrypt that file, but not mine...difficult.
What version are you using?? could that effect anything?I'm using seahorse 2.20.1 



---

### Post by Xavieran on 2008-01-11
Which part of gpg --list-keys is the key ID?:)

---

### Post by Dr Small on 2008-01-11
Ok. So I finally was able to read the message from launchpad.
I went in and canceld that key activation, and re-entered my fingerprint again.

This time I was able to read the GPG. But, I still can't read anything from seventhc.
Maybe my key was corrupted that I gave you? I dunno.

Anyhow, my public key can be found here:
[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xBC9850A926FD8AF9](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xBC9850A926FD8AF9)

Dr Small

---

### Post by Xavieran on 2008-01-11
Which ports would gpg send the key to keyserver.ubuntu.com?

I have tried syncing my keys with various keyservers but I get a connection failed...I know this is my router blocking packets (it happened for IRC and Telnet...) and if I can find out the ports it uses all will be well...:)

P.S...I figured out which part is the keyy id...xD

---

### Post by seventhc on 2008-01-11
Do you want me to try sending you another encrypted email?

---

### Post by Xavieran on 2008-01-11
Whoohooo...I figured out which port it uses for anyone interested:11371

And here is my key...[http://keyserver.ubuntu.com:11371/pks/lookup?search=0x915ABF59&op=index]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0x915ABF59&op=index")

---

### Post by Dr Small on 2008-01-11
> **Xavieran said:**
> Which ports would gpg send the key to keyserver.ubuntu.com?

I have tried syncing my keys with various keyservers but I get a connection failed...I know this is my router blocking packets (it happened for IRC and Telnet...) and if I can find out the ports it uses all will be well...:)

P.S...I figured out which part is the keyy id...xD
Try port 11371.

@seventhc, yes, you can send me another encrypted email, by using the above key and see if it actually works now ;)

Dr Small

---

### Post by seventhc on 2008-01-11
did you update [http://php.8ez.com/drsmall/public.key](http://php.8ez.com/drsmall/public.key)
or can i still use that?

nevermind, i see the new key. :D

---

### Post by Xavieran on 2008-01-11
Dr Small:Could you test my key out...ie,encrypt it and then try to decrypt it and then encrypt a file and send it to me...thanks:)

---

### Post by Dr Small on 2008-01-11
I sent you an GPG message via PM. If you could do the same, I would be obliged, just to see if we are actually getting somewhere now :)

Dr Small

---

### Post by Xavieran on 2008-01-11
I failed to do it the cool way you did,so...

The file is attached again just rename it with a .gpg on the end...

---

### Post by Dr Small on 2008-01-11
> **Xavieran said:**
> I failed to do it the cool way you did,so...

The file is attached again just rename it with a .gpg on the end...
Umm, that was an empty archive.

---

### Post by Xavieran on 2008-01-11
Was it?

It was meant to be a text file ...

Just rename it again and decrypt it...

---

### Post by Dr Small on 2008-01-12
Thanks for all the help guys. I'm going to mark this thread as Solved since my problems are over ;)
Hey, I even wrote an article on my blog about it, to help others and remind myself :)
[http://php.8ez.com/drsmall/blog/?p=209](http://php.8ez.com/drsmall/blog/?p=209)

Thanks again for the help!
Dr Small

---

### Post by drs305 on 2008-01-12
Dr Small,

I took a look at your blog. You have a great layman's explanation of GPG and how to use it. 

True to the ubuntu community, you started with a question and ended up creating something that will help others. 

Thanks!

---

### Post by kevdog on 2008-01-13
Dr Small

Seems like you have mastered the basics and ready to move onto the advanced topics.  Just for security sakes Id recommend you creating 4096 bit RSA signing and encryption keys and change your default cipher and hash preferences.  If you are really up to it, you can compile the stable branch of gnupg from svn/cvs in order to add the camellia cipher to your group of possible cipher types.  

Im not trying to blow you away with details, however I think the default options for key creation could be better (DSA/Elgamal 1024 bit keys).  I think a hash other than the SHA1 (like SHA256) would be a better choice, and a ciphers such as AES256, CAMELLIA256(experimental), or TWOFISH would be a better choice.

Again Im not trying to get technical, however if you are going to the trouble to use gpg, you might as well do it write.  

Ive written a tutorial how to compile and install gnupg from source (stable branch):
[http://ubuntuforums.org/showthread.php?t=649466&highlight=gpg](http://ubuntuforums.org/showthread.php?t=649466&highlight=gpg)

Hope this helps

---

### Post by Scott_fakename on 2008-01-13
> **Dr Small said:**
> Thanks for the help, and I have read those links already. I can encrypt my own text with my public key, and then decrypt it with my private key, but when I sent my fingerprint to launchpad to verify my key, they said that I needed to decrypt it with my private key.

So far, I have yet to be able to decrypt it. Here is what they sent me, but nothing I have tried so far will decrypt it:



Everything I try, says No data.
Also, if I want someone to encrypt a message to me, do I give them my armored key, or "26FD8AF9" ?

What I would do is copy that information, from "--begin..." to "end---..." and paste it into a text file, and then run GPG on that file.

I don't know the exact arguments you would need to pass, though. Sorry about that.

---

