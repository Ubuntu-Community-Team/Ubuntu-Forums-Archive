---
title: "voice commanding in Ubuntu"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-03-16
Is there Voice commanding software in Ubuntu? If yes what is that and how to use it?

---

### Post by adi_das on 2008-03-16
anyone?

---

### Post by adi_das on 2008-03-16
How to Change voice in ESPEAK

---

### Post by gobbles414 on 2008-03-16
> **adi_das said:**
> Is there Voice commanding software in Ubuntu? If yes what is that and how to use it?

I've researched this topic a bit. All of the native Linux voice recognition programs that I've researched are either old or incomplete. If you just need voice recognition for word processing and emails, you can run Dragon Naturally Speaking in [Wine]("http://www.winehq.org/"). You should be able to install Wine in Ubuntu by using *Applications => Add/Remove* or *System => Administration => Synaptic Package Manager*.

EDIT: I cannot help you if you need a program that will allow you to command you computer's mouse with your voice. But... I'm far from an expert on this topic. So I'd be interested to read ideas from other Ubuntu users.

EDIT: By the way, it often takes a few hours or more for people to respond to questions in the forums. So please be patient. You can always use a service like IRC if you need an immediate response.

---

### Post by durand on 2008-03-16
```
durand@Carbon-14:~$ espeak --voices
Pty Language Age/Gender VoiceName       File        Other Langs
 5  af             M  afrikaans         af          
 7  af             M  afrikaans-mbrola-1 mb/mb-af1   
 5  bs             M  bosnian           bs          
 5  cs             M  czech             cs          
 7  cs             M  czech-mbrola-2    mb/mb-cz2   
 5  cy             M  welsh-test        cy          
 5  de             M  german            de          
 6  de             M  german-mbrola-4   mb/mb-de4   
 6  de             M  german-mbrola-6   mb/mb-de6   
 7  de             F  german-mbrola-5   mb/mb-de5   
 7  de             F  german-mbrola-7   mb/mb-de7   
 5  el             M  greek             el          
 7  el             M  greek-mbrola-1    mb/mb-gr2   
 5  en             M  default           default     
 5  en             F  en-german-5       mb/mb-de5-en 
 5  en             F  en-swedish-f      mb/mb-sw2-en 
 7  en             M  en-greek          mb/mb-gr2-en 
 9  en             M  en-german         mb/mb-de4-en 
 9  en             M  en-romanian       mb/mb-ro1-en 
10  en             M  en-dutch          mb/mb-nl2-en 
10  en             F  en-french         mb/mb-fr4-en 
10  en             M  en-french         mb/mb-fr1-en 
10  en             F  en-hungarian      mb/mb-hu1-en 
11  en             M  en-afrikaans      mb/mb-af1-en 
11  en             F  en-polish         mb/mb-pl1-en 
11  en             M  en-swedish        mb/mb-sw1-en 
 5  en-r           M  en-rhotic         en/en-r     (en 3)
 5  en-sc          M  en-scottish       en/en-sc    (en 4)
 2  en-uk          M  english           en/en       (en 2)
 3  en-uk          M  english-mb-en1    mb/mb-en1   (en 2)
 5  en-uk-north    M  lancashire        en/en-n     (en-uk 3)
 5  en-uk-rp       M  english_rp        en/en-rp    (en-uk 4)
 5  en-uk-wmids    M  english_wmids     en/en-wm    
 5  en-us          F  us-mbrola-1       mb/mb-us1   (en 8)
 5  en-us          M  us-mbrola-2       mb/mb-us2   (en 7)
 5  en-us          M  us-mbrola-3       mb/mb-us3   (en 8)
 5  en-wi          M  en-westindies     en/en-wi    (en-uk 4)
 5  eo             M  esperanto         eo          
 5  es             M  spanish           es          
 5  fi             M  finnish           fi          
 5  fr             M  french            fr          
 7  fr             M  french-mbrola-1   mb/mb-fr1   
 7  fr             F  french-mbrola-4   mb/mb-fr4   
 5  grc            M  greek-ancient     grc         
 6  grc            M  german-mbrola-6   mb/mb-de6-grc 
 5  hi             M  hindi-test        hi          
 5  hr             M  croatian          hr          (hbs 5)
 7  hr             M  croatian-mbrola-1 mb/mb-cr1   
 5  hu             M  hungarian         hu          
 7  hu             F  hungarian-mbrola-1 mb/mb-hu1   
 5  is             M  icelandic-test    is          
 5  it             M  italian           it          
 7  it             M  italian-mbrola-3  mb/mb-it3   
 7  it             F  italian-mbrola-4  mb/mb-it4   
 5  jbo               lojban            jbo         
 5  la             M  latin             la          
 7  la             M  latin-mbrola-1    mb/mb-la1   
 5  mk             M  macedonian-test   mk          
 5  nl             M  dutch-test        nl          
 7  nl             M  dutch-mbrola-2    mb/mb-nl2   
 5  no             M  norwegian-test    no          (nb 5)
 5  pl             M  polish_test       pl          
 7  pl             F  polish-mbrola-1   mb/mb-pl1   
 5  pt             M  brazil            pt          (pt-br 5)
 5  pt-pt          M  portugal          pt-pt       
 5  ro             M  romanian          ro          
 7  ro             M  romanian-mbrola-1 mb/mb-ro1   
 5  ru             M  russian_test      ru          
 5  sk             M  slovak            sk          
 5  sr             M  serbian           sr          
 5  sv             M  swedish           sv          
 7  sv             M  swedish-mbrola-1  mb/mb-sw1   
 8  sv             F  swedish-mbrola-2  mb/mb-sw2   
 5  sw             M  swahihi-test      sw          
 5  vi             M  vietnam-test      vi          
 5  zh             M  Mandarin test     zh          
 5  zh-yue         M  cantonese-test    zhy         (yue 5)

```

Basically, just add the 2 letter code to the end of this: "espeak -v "

---

### Post by adi_das on 2008-03-16
I installed gnome-voice-control but i dont know how to open it?

---

### Post by MasterJS on 2008-03-16
type that exact name into a terminal and it should open

---

### Post by adi_das on 2008-03-16
It says command not found

---

### Post by bsharp on 2008-03-16
gnome-voice-control is an appelet (<sp?), just right click on a GNOME panel and select Add to Panel, and look for it in the window that opens.

---

### Post by adi_das on 2008-03-16
How to use it?

---

### Post by bsharp on 2008-03-16
lol sorry, i have no idea.  My guess would be to click it to activate the voice control, but there is probably some kind of calibration that you have to do.

---

### Post by adi_das on 2008-03-17
Anyone?

---

### Post by rpainter on 2008-03-17
Dude...Google is your friend!!!

Type "[gnome voice control]("http://www.google.com/search?q=gnome+voice+control&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a")" in the search, and you will find some stuff about it.

---

### Post by gobbles414 on 2008-03-17
> **adi_das said:**
> Anyone?

There is a YouTube video of how to use gnome-voice-control [here]("http://www.youtube.com/watch?v=GCSgkUnlGGA"). This program seems to be in the beginning stages of development. But perhaps speech recognition will be coming to Linux eventually after all. Let us know if this program works for you.

PS: Please, please, please be aware of some general rules here in the forums. First, the forums are NOT a LIVE help area for Ubuntu. You should use IRC for that. So, you should wait at least 24 hours before posting bumps (e.g. "Anyone?") in the forums. There should be a messaging program called *Pidgin* on your computer that allows you to access IRC. Click [here]("http://www.ubuntu.com/support/community/chatirc") for more info. Also, it's best for everyone if you DO NOT create multiple threads for a single problem. You'll find that obeying the forums' rules will encourage the smartest people to reply to your questions.

---

