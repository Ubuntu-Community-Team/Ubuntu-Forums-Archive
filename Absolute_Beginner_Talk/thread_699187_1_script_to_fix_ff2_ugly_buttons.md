---
title: "1 script to fix ff2 ugly buttons"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2008-02-17
ok, so there is a ton of info out there how to do this, i just made a script (hey maybe there already is a script!) that just executes these commands:

```
% cd /tmp
% wget http://users.tkk.fi/~otsaloma/art/firefox-form-widgets.tar.gz
% tar -xvzf firefox-form-widgets.tar.gz
% sudo cp /usr/share/firefox/res/forms.css /usr/share/firefox/res/forms.css.bak
% cat firefox-form-widgets/res/forms-extra.css | sudo tee --append /usr/share/firefox/res/forms.css > /dev/null
% sudo cp -r firefox-form-widgets/res/form-widgets /usr/share/firefox/res
% rm -rf firefox-form-widgets
```

That I copied from ubuntutips.net, anyway attached is the sh

sh fixffbuttons.sh

sv

p.s. if you want to run a ton of commands in sequence at once i suggest making a script for it, you just seperate them with ; semicolans; :)

---

### Post by sb12 on 2008-02-17
> **staticvoid said:**
> ok, so there is a ton of info out there how to do this, i just made a script (hey maybe there already is a script!) that just executes these commands:

```
% cd /tmp
% wget http://users.tkk.fi/~otsaloma/art/firefox-form-widgets.tar.gz
% tar -xvzf firefox-form-widgets.tar.gz
% sudo cp /usr/share/firefox/res/forms.css /usr/share/firefox/res/forms.css.bak
% cat firefox-form-widgets/res/forms-extra.css | sudo tee --append /usr/share/firefox/res/forms.css > /dev/null
% sudo cp -r firefox-form-widgets/res/form-widgets /usr/share/firefox/res
% rm -rf firefox-form-widgets
```

That I copied from ubuntutips.net, anyway attached is the sh

btw, is this called bash?

sv

bash is a shell

---

### Post by staticvoid on 2008-02-17
right.


woops  :P

so what i made is called a script? it just executes commands in sequence?

i'm not a hacker by far :)

lol

sv

---

### Post by sb12 on 2008-02-17
> **staticvoid said:**
> right.


woops  :P

so what i made is called a script? it just executes commands in sequence?

i'm not a hacker by far :)

lol

sv

yes it's a shell script ;)

---

### Post by staticvoid on 2008-02-17
lol.. should i put
> !#bash/sh
at the top or somthing?

sv

---

### Post by sb12 on 2008-02-17
#!/bin/bash is what I would use, or switch bash with sh depending on the shell; so like #!/bin/sh

---

### Post by staticvoid on 2008-02-19
lol.. just installed arch and was looking for my ff2 ugly buttons fix script... here tis...

sv

---

