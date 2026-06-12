---
title: "Brazilian portugues on US keyboard"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by danielferber on 2006-04-27
Hi! It sounds like a very silly question that is driving me mad...

How do I type Brazilian accents (ã, á, é, etc) and German Umlaut (ä, ö, ü) on and US keyboard (IBM Thinkpad T42)?

I have already installed language support for German and Portuguese, and also have played with keyboard layouts on the configuration menu.

After seaching one night long on internet I cound not figure out how. I found some cryptic tutorials how to edit xorg conf files, but they didnt sound like for human being.

Thanks,
Daniel FF

---

### Post by mostwanted on 2006-04-27
On my keyboard (Danish) circumflex, umlaut and the tilde (~ thing) are available from the key in the corner between backspace and return/enter.

Accent egy and the one that goes the other way are available on the key next to backspace.

As neither of those accents (except egy occasionally) are used in Danish, I suspect it's similar on the US keyboard and that they are included as part of a general latin keyboard layout.

---

### Post by danielferber on 2006-04-27
I have found the key for accents. But when I press ~ and then 'a', I dont get 'ã', but '~a' instead. Applying latin layout solves the problem of writing umlaut and accents, but the keys do no more write what they show. I have tried the command: setxkbmap -model pc104 -layout us -variant intl, but when I press '´' and 'c' I dont get 'ç' , but c-acute, that does not exist in Portuguese. On gentoo, this configuration is trivial. I dont understand why ubunto does not support this easily. I really dont understand why I even have to configure it if I have chosen "Brasil" on the first installation step!

---

### Post by mostwanted on 2006-04-27
It works on my box, can't say what's wrong.

---

### Post by danielferber on 2006-04-27
You are using a Danish keyboard, and I suppose that Ubuntu uses accents and umlauts by default, as some of them are needed for Danish.
But on American keyboard, no accents and umlauts are allowed and there is no user friendly way to solve this in Ubunto.

---

### Post by mostwanted on 2006-04-27
[QUOTE=danielferber]You are using a Danish keyboard, and I suppose that Ubuntu uses accents and umlauts by default, as some of them are needed for Danish.
But on American keyboard, no accents and umlauts are allowed and there is no user friendly way to solve this in Ubunto.[/QUOTE]

Obviously, you didn't read my post; Danish doesn't use accents and umlauts. But, putting that aside for the moment:

If the key is there, of course it's allowed. Either you're doing something wrong or something's wrong with your Ubuntu setup. Have you tried switching to a different keyboard layout? I see several versions of the US keyboard when I look in the keyboard settings.

---

### Post by danielferber on 2006-04-27
After all, I found a solution! It took only one day of research how to get my computer to work for Brazilian Portuguese. Really disappointing for a human being Linux. But this is not the main point of my post.

First I installed complete kubunto! Fortunately kubunto  comes with some support for non English languages on US-keyboard. Stantard Ubuntu installation does not provide any variants for US-keyboard. Now I am using US-intl. It solved most Brazilian accents, but not "ç", that was mapped to alt+comma instead of acute+c.

Second problem was solved by installing Brazilian Portuguese language support in order to log-in in as Brazilian Portuguese language with an US-intl-keyboard. Suddenly "ç" stated working.

It is quite inconvinient since I like using German and English for my desktop, but want to still write in Portuguese.

In short, I believe that Ubutu people must think again over language and keyboard configuration, since the current installation process is at least very dumb.

Considering that I have chosen Brazil on installation, I wonder:
1) Why Ubunto has not installed Brazilian Portuguese language by default, why I had t download by myself.
2) Why have to configure my keyboard manually to Brazilian letters, even worse, why I had to install Kubunto to be able to select US-intl-keyboard.
3) How may an newbe guess that he must log-in in some special language, keyboard layout and variat combination in order to get right keyboard rules for pt_BR-UTF...

After all, I was right: mostwanted keyboard works as expeted because he was lucky. If the had an US-keyboard and wanted to write "ç", he couldn't. By example, I am proving that, depending on your keyboard, county and gnome language, sometime it works, and sometime not. A better way is to be found.

---

