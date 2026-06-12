---
title: "How to activer SCIM?"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by ytt on 2006-06-25
I tape ctrl+space, shift+space...and I see nothing appear. What can i do?

---

### Post by FredB on 2006-06-25
[QUOTE=ytt]I tape ctrl+space, shift+space...and I see nothing appear. What can i do?[/QUOTE]

I have something which I am translating into english, I won't be sure it will work at 100% :)

1) Installing packages, in terminal :

```
sudo apt-get install scim-chinese scim-gtk2-immodule xfonts-intl-chinese
```

If you want japanese, modify the packages :)

2) You have to create (or modify) a file named .xsession in your home directory, adding this :

```
scim -d
export XMODIFIERS=@im=scim
export GTK_IM_MODULE=scim
gnome-session
```

Make it executable with a little **chmod +x .xsession**

Then close your gnome session and restart it. SCIM will work. As you don't tell which ubuntu you're using, I supposed it was Ubuntu, not Kubuntu.

Hope it helped you.

---

### Post by erik-the-red on 2006-07-02
How can I adapt that for Xubuntu?

---

### Post by drtvasudevan on 2006-07-03
system>preferences>scim setup
i am not sure abt xubuntu.
this is for ubuntu

tv

---

### Post by Blur-king on 2006-07-03
You may want to try **[https://help.ubuntu.com/]("https://help.ubuntu.com/")**  . Click the **community docs** and then  type **scim** into the search box. It was very helpful for me.

---

### Post by mogliii on 2006-07-04
Hi,

I have lately installed a totally fresh Xubuntu in english.

After the Installation, if you type 
```
$ locale -a
C
POSIX
```

But as I read in many places, you need utf8 locales (ja_JP and for example en_GB).

So, you have to install packages. What you should NOT! do is to install
```
language-support-ja #DON'T INSTALL
```
because this will install everything like openoffice language support as this seems to be the (g)ubuntu package. But as you use Xubuntu and you want a fast, slim system, we dont want this.

Install the following:
```
$ sudo apt-get install im-switch scim-anthy scim-qtimm
$ sudo apt-get install language-pack-en language-pack-en-base language-pack-ja language-pack-ja-base mozilla-firefox-locale-en-gb mozilla-firefox-locale-ja mozilla-firefox-locale-ja-jp 
```
... just look in synaptic for ja but be careful not to install too much

if you installed everything, start your x-session again with Ctr+Alt+Backspace. (Save data before)

In the login screen, choose the language option and choose English (GB) and log in as usual. (make the choice default)

Back in Xubuntu, open a terminal and type the following:
```
$ im-switch -z en_GB -s scim
$ im-switch -z en_GB scim-anthy
```

restart X-session again, and if you open firefox, you should see a grey keyboard in the systray.
When pressing Ctr+Space, the grey keyboard should change to a golden crown. and start typing!

Note: I can not guarantee that this works. And I didnt take exact notes what I was doing to get it working. So please give me feedback and if it does not work, I will try to find the mistake.

&#12364;&#12435;&#12400;&#12387;&#12390;&#12288;&#12367;&#12384;&#12373;&#12356;&#65281;

---

### Post by mogliii on 2006-07-04
Hi,

just remembered one thing I forgot in my previous post:

after installing the language things, and getting back into xubuntu, you have to go to the language support (in system), and choose a default language. choose english GB. And if he complains, that not all packages are installed, let him install after you checked it. be careful openoffice and stuff dont getinstalled.

I also noticed that for english, there is no hook, only a dash. This should not bother you any furhter. I guess this becomes only a hook when all packages for gnome would be installed, as the language support dialog is taken from gnome.

hope it helps

---

