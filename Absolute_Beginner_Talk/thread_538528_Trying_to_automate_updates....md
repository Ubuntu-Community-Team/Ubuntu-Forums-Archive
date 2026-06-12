---
title: "Trying to automate updates..."
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by blop on 2007-08-30
I am trying to automate updates in ubuntu....so i installed Schedule which i think is a cron or such front end.

I made two entries...

1. ls sudo aptitude update
2. ls sudo aptitude upgrade

However these dont seem to work....

can anyone help?

---

### Post by chuckyp on 2007-08-30
ls is for listing a directory or files.  The commands should just be:
```

sudo apt-get update && sudo apt-get upgrade

```

However, you are going to run in to issues when those commands need the root password.  You would have to the commands run as a priveleged user.

---

### Post by blop on 2007-08-30
i see...

so is there no way i can make updates just work without any input.....even putting the admin password in?

it kind of misses the point of the automation if i have to be there putting the password in..

cheers

---

### Post by justleen on 2007-08-30
> **blop said:**
> i see...

so is there no way i can make updates just work without any input.....even putting the admin password in?

it kind of misses the point of the automation if i have to be there putting the password in..

cheers

yes there is...

try this:
open a terminal and give a 
```
sudo -i
```

after which you  enter
```
crontab -e
```
crontab is the system scheduler. I wont go into any [details]("http://www.google.nl/search?q=crontab+howto") there are whole books written on the subject. 
Press "i" once to go into edit mode
copy paste (paste is ctrl-shift-v in terminal) this line
```
01 00 * * *  apt-get update && apt-get upgrade
```

press esc once, and then type ":" (a colon apears at the bottom) and then "wq" with an <enter>
it will output "New crontab installed"
this wil execute the update every night @ 00:01. the thing here is, your doing it as root, in the root schedule. This means it will not ask for a passwd (you entered that with the sudo -i). just ype exit to leave "root-mode"
  
there you go...

---

### Post by pitje on 2007-08-31
there's also the -y flag in apt-get, which automatically answers 'yes' to all prompts.

if you do a man apt-get, you'll get to see more of those flags 

........  -y, --yes, --assume-yes
          Automatic yes to prompts; assume "yes" as answer to all prompts and
          run non-interactively. If an undesirable situation, such as changing
          a held package, trying to install a unauthenticated package or
          removing an essential package occurs then apt-get will abort.
          Configuration Item: APT::Get::Assume-Yes.
.........

---

