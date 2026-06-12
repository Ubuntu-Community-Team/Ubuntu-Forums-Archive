---
title: "I've been logging in as root till now.."
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Fataltragedy2 on 2007-03-18
I've been logging in as root because I want to be able to have complete access to my system. Are there any security consequences in doing so? would you advise it? thanks.

---

### Post by ThrobbingBrain66 on 2007-03-18
> **Fataltragedy2 said:**
> I've been logging in as root because I want to be able to have complete access to my system. Are there any security consequences in doing so? would you advise it? thanks.

Even when you don't log in as root, you still have access to your system...you just have to use a password to modify system files.

No one here will recommend running as root all the time however.  Doing this allows spyware, malware, viruses, hackers, etc to have free run of your system and they can do whatever they want.  May as well be running Windows in Administrator mode.

---

### Post by oilchangeguy on 2007-03-18
yes. that's the main problem with security in windows. by default in ubuntu no root id is created. when run as user yo have to enter your password to perform admin tasks. not so when you use root. the computer is wide open all the time.

---

### Post by Fataltragedy2 on 2007-03-18
Yes, but whats the chance of me getting a virus on Ubuntu? I heard the risk is very very low unless you're installing packages outside the repos. which I haven't done. I've configured iptables and firestarter and all I download are media files. 

The thing is I'm not used to the terminal (yet.) so I can't use sudo commands without running into a roadblock (For example when mounting files. or accessing a mounted drive.)

---

### Post by Kobalt on 2007-03-18
> **Fataltragedy2 said:**
> The thing is I'm not used to the terminal (yet.) so I can't use sudo commands without running into a roadblock (For example when mounting files. or accessing a mounted drive.)
And yet you managed to get a root account working in Ubuntu ? :confused: I thought that Ubuntu didn't allow by default to have a root account... 

You have very few concerns to have about viruses on Linux... You might take really good precautions at what you do however, if all your sessions are run with root privileges a wrong manipulation might screw up your system real badly.

---

### Post by Fataltragedy2 on 2007-03-18
> **Kobalt said:**
> And yet you managed to get a root account working in Ubuntu ? :confused: I thought that Ubuntu didn't allow by default to have a root account... 

You have very few concerns to have about viruses on Linux... You might take really good precautions at what you do however, if all your sessions are run with root privileges a wrong manipulation might screw up your system real badly.

I'm good with GUI's :p I accessed root through GUI.

---

### Post by Kobalt on 2007-03-18
So what you did was giving your user account the root privileges, not actually logging as root into a session...

---

### Post by sad_iq on 2007-03-18
It's not (only) viruses you have to worry with ubuntu(or linux for that matter), every program that runs as root will have access to the whole system, so if anybody takes controll of that program will have the same privilege as the program(root privilege), and even a (very) good iptables setup won't prevent that from happening someday.
 ...and also...multimedia files can contain viruses(backdoors, troyans and all that)...so **DON'T RUN AS ROOT**

---

### Post by Fataltragedy2 on 2007-03-18
Okay, Will switch now.

---

### Post by Fataltragedy2 on 2007-03-18
> **Kobalt said:**
> So what you did was giving your user account the root privileges, not actually logging as root into a session...

Nope, All I did was go into the User manager, set a root password and login with user: root.

---

### Post by Fleshy on 2007-03-18
> **Fataltragedy2 said:**
> Nope, All I did was go into the User manager, set a root password and login with user: root.

i thought that it's impossible (in X)! I'm not right?

---

### Post by Fataltragedy2 on 2007-03-18
> **Fleshy said:**
> i thought that it's impossible (in X)! I'm not right?

Well I did it :p

---

### Post by bapoumba on 2007-03-18
> **Fataltragedy2 said:**
> I've been logging in as root because I want to be able to have complete access to my system. Are there any security consequences in doing so? would you advise it? thanks.
Please read [this]("https://help.ubuntu.com/community/RootSudo").

---

### Post by Sbarton on 2007-03-18
Did anything happen to Fataltragedy1?

---

### Post by bapoumba on 2007-03-18
> **Sbarton said:**
> Did anything happen to Fataltragedy1?
??

---

### Post by Kobalt on 2007-03-18
I think it's nickname-joke related to the security concerns...

---

### Post by Sbarton on 2007-03-19
Kobalt got it! It was a lighthearted joke, no offence meant.
regards

---

