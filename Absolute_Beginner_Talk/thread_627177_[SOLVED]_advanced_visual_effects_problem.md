---
title: "[SOLVED] advanced visual effects problem"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by Fanin on 2007-11-29
ok.. if I understand this whole thing right, the "cube" desktop is already installed in gutsy, right? all i need to do is go to "add/remove" and find "ccsm" and install that to get more advanced desktop effects.. but every time i try to mark the "ccsm" program the "add/remove" program refreshes and leaves the "ccsm" program unmarked
hope you understand.. please help :(

---

### Post by bjarneh on 2007-11-29
system-->options-->apperance-->visual effects

then you can go fancy with Extra, i don't think that gives you the cube however, but this is a matter of installing

compizconfig-settings-manager
compiz-fusion-plugins-extra

which gives you another option (Custom) then you can click on the stuff you want, which in your case seems to be the Cube :-)

---

### Post by Fanin on 2007-11-29
> **bjarneh said:**
> system-->options-->apperance-->visual effects

then you can go fancy with Extra, i don't think that gives you the cube however, but this is a matter of installing

compizconfig-settings-manager
compiz-fusion-plugins-extra

which gives you another option (Custom) then you can click on the stuff you want, which in your case seems to be the Cube :-)

where and how do I install the compiz things?
I can't find them in "synaptic package manager" nor "add/remove applications" :confused:

---

### Post by LaRoza on 2007-11-29
```

sudo aptitude install compizconfig-settings-manager
sudo aptitude install compiz-fusion-plugins-extra

```

---

### Post by Fanin on 2007-11-29
> **LaRoza said:**
> ```

sudo aptitude install compizconfig-settings-manager
sudo aptitude install compiz-fusion-plugins-extra

```

that's cool..... now what :confused:

---

### Post by satelight 7430 on 2007-11-29
now try " start-compiz manager"

---

### Post by Fanin on 2007-11-29
> **satelight 7430 said:**
> now try " start-compiz manager"

"command not found".. however if I type "start compiz-manager" it says "need to be root"
now what?

---

### Post by Fanin on 2007-11-30
Does it for some reason not work on ATI Radeon ???

---

### Post by Fanin on 2007-11-30
bump :)

---

### Post by vikramsharma on 2007-11-30
> **Fanin said:**
> "command not found".. however if I type "start compiz-manager" it says "need to be root"
now what?

try using sudo command before typing in any system commands for example "sudo start-compiz manager" (without the quotes), or you could goto the "System" Menu in there goto "Preferences" and look for "Advanced Desktop Effects Settings" that is your compizsettings manager.  You can also try running ccsm through terminal if you encounter a message stating "You need to be root" just type in "sudo ccsm".  Hope I clarified some of your doubts.

---

### Post by Fanin on 2007-11-30
> **vikramsharma said:**
> try using sudo command before typing in any system commands for example "sudo start-compiz manager" (without the quotes), or you could goto the "System" Menu in there goto "Preferences" and look for "Advanced Desktop Effects Settings" that is your compizsettings manager.  You can also try running ccsm through terminal if you encounter a message stating "You need to be root" just type in "sudo ccsm".  Hope I clarified some of your doubts.

I did try using sudo before typing start compiz-manager and it said "unknown job", and if i go to System>Preferences: there is nothing called "Advanced Desktop Settings" and i did try typing "sudo start ccsm" and it said "unknown job" again :(

---

### Post by Skairaven on 2007-11-30
I just put compizconfig-settings-manager in to the synaptic doowhatsit.

---

### Post by Fanin on 2007-11-30
> **Skairaven said:**
> I just put compizconfig-settings-manager in to the synaptic doowhatsit.

what exactly is a "doowhatsit" ?
I tried searching for it in the synaptic package manager (I just guessed that's what you meant) and didn't find anything

---

### Post by Skairaven on 2007-11-30
Really? I cannot remember exactly what I searched for. It was xxxxx-settings-manager
Try the second two and see what comes up?
Honestly I am just spinning ideas, I started using Ubuntu all of a day ago.

---

### Post by vikramsharma on 2007-11-30
> **Fanin said:**
> I did try using sudo before typing start compiz-manager and it said "unknown job", and if i go to System>Preferences: there is nothing called "Advanced Desktop Settings" and i did try typing "sudo start ccsm" and it said "unknown job" again :(

Just a query have you installed compizconfig-settings-manager through Synaptic Package Manager.  In case you have not, goto Synaptic Package Manager and look for "compizconfig-settings-manager".  Please do reply becasue I am a bit unclear about whether you have compizconfig-settings-manager installed or not.

---

### Post by Fanin on 2007-11-30
when i search for compiz in "Synaptic manager" if find something, but it's all installed, but there is nothing in the System>Preferences that is called "advanced desktop settings" or if i click on "apperance" and under the tab "visual effects" the only thing i can choose from is "none/normal/extra" and there is nothing called "preferences" in that tab :confused:
hope that explains something

---

### Post by Fanin on 2007-11-30
> **vikramsharma said:**
> Just a query have you installed compizconfig-settings-manager through Synaptic Package Manager.  In case you have not, goto Synaptic Package Manager and look for "compizconfig-settings-manager".  Please do reply becasue I am a bit unclear about whether you have compizconfig-settings-manager installed or not.

I don't find anything called exactly "compizconfig-settings-manager" but some other compiz stuff :confused:

---

### Post by Skairaven on 2007-11-30
What other compiz ones?

---

### Post by Fanin on 2007-11-30
> **Skairaven said:**
> What other compiz ones?

libcompizconfig0
compiz-fusion-plugins-extra
compiz-fusion-plugins-main
libcompizconfig-backend-gconf
libdecoration0
compiz-plugins
compiz
compiz-core
compiz-gnome

those other compiz ones

---

### Post by Skairaven on 2007-11-30
Compiz-Fusion-plugins-extra

Judging by name alone, that one looks like it will give you the extra things.

---

### Post by Fanin on 2007-11-30
> **Skairaven said:**
> Compiz-Fusion-plugins-extra

Judging by name alone, that one looks like it will give you the extra things.

:) guess i forgot to mention.. they are all marked as installed

---

### Post by Skairaven on 2007-11-30
Then I have less then no idea. Sorry I can not be of service.

---

### Post by Fanin on 2007-11-30
WOHOO i think i did it
I opened "add/remove app." and clicked on preferences and checked two of the top checkboxes and installed ccsm.. I can now open advanced desktop settings:guitar:

---

### Post by Fanin on 2007-11-30
> **Skairaven said:**
> Then I have less then no idea. Sorry I can not be of service.

thank you very much for your help :)

---

