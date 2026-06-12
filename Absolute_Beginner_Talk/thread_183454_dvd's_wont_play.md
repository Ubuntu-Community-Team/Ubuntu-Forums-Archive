---
title: "dvd's wont play"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by caffiend on 2006-05-28
tried toload totem xine and get error depends: libxinelc2 but it is not going to installed
when I try to play a  DVD I get the error totem has quit unexpectedly and I cant seem to inform developers
I have tried running sudo apt-get update

---

### Post by user1397 on 2006-05-28
[quote=caffiend]tried toload totem xine and get error depends: libxinelc2 but it is not going to installed
when I try to play a  DVD I get the error totem has quit unexpectedly and I cant seem to inform developers
I have tried running sudo apt-get update[/quote]
have you read the page: [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats) ?

---

### Post by jazzmuzik on 2006-05-28
You've misspelled the library and it's hard to tell if that's the problem or not. There is no libxinelc2 with an L, but there is a libxine1c2 with a one.

Compare:

libxinelc2
libxine1c2

---

### Post by caffiend on 2006-05-28
yes of course you advised me earlier and I have done my homework you were the one who told me to run the sudo apt-get udate which I did as well as try to install the totem xine but I get the error message

---

### Post by caffiend on 2006-05-28
[QUOTE=jazzmuzik]You've misspelled the library and it's hard to tell if that's the problem or not. There is no libxinelc2 with an L, but there is a libxine1c2 with a one.

Compare:

libxinelc2
libxine1c2[/QUOTE]

you are right it is libxine1c2  do you have a suggestion about this problem?

---

### Post by user1397 on 2006-05-28
[quote=caffiend]you are right it is libxine1c2  do you have a suggestion about this problem?[/quote]
well you should install it for starters:)

---

### Post by caffiend on 2006-05-28
[QUOTE=erik1397]well you should install it for starters:)[/QUOTE]
tried but it says it can't or wont 
error message  Depends: libxine1c2 but it is not going to be installed
I don't understand why it just says f**k you not going to do it.
very frustrating

---

### Post by jazzmuzik on 2006-05-28
what command did you use to install it?

---

### Post by caffiend on 2006-05-28
[QUOTE=caffiend]tried but it says it can't or wont 
error message  Depends: libxine1c2 but it is not going to be installed
I don't understand why it just says f**k you not going to do it.
very frustrating[/QUOTE]
 
it took me like ten hours but now I think I understand what you were saying (install libxine1c2) so I tried that and got this message
Depends: libmodplug0c2 (>=1:0.7-4.1) but it is not installable
](*,)

---

### Post by caffiend on 2006-05-28
[QUOTE=jazzmuzik]what command did you use to install it?[/QUOTE]

using the synap. pack. man.  also when I mark it for download it says 
to be removed
rythmbox
totem
totem gstreamer
ubuntu-desktop

which I have the feeling I will want and have to reinstall later

---

### Post by user1397 on 2006-05-28
you shouldn't even need totem xine.  i use regular totem and i can play dvd's on it just fine.  it worked for me after i did what the restricted formats page said i should do.

---

### Post by jazzmuzik on 2006-05-28
I'm wondering if you need the libdvdcss2 library. Isn't that necessary for dvd decryption, i.e., playing?

---

### Post by caffiend on 2006-05-30
I finally just reloaded and that worked should have done it days ago. Guess it just goes to show sometimes you gotta just scrap it and start over no matter what the OS is.

[QUOTE=jazzmuzik]I'm wondering if you need the libdvdcss2 library. Isn't that necessary for dvd decryption, i.e., playing?[/QUOTE]

---

### Post by richbarna on 2006-05-30
Ok, just install the latest Automatix :-
[Download the .deb file here]("http://www.beerorkid.com/arnieboy/automatix_6.0-5rc4_i386.deb")
When you've got it, go to where the file is, open your terminal/konsole and type this :-
> sudo dpkg -i automatix_6.0-5rc4_i386.deb

Automatix will do everything for you :)

---

