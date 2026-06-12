---
title: "scim not working"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by linuxnewbie999 on 2008-03-19
SCIM won't work no matter how i configure it. I tried trigger key or by clicking it but no language options come out...  How to fix this???

---

### Post by Kiri on 2008-03-19
You set up the additional languages and locale stuff in ubuntu?

---

### Post by linuxnewbie999 on 2008-03-19
Yes. I believed i did. I can select korean language options but it just won't works..

---

### Post by Kiri on 2008-03-20
What I did to get Japanese working was:
-System>Administration>Language Support
-Tick the box for Korean in your case
-Reload X (ctrl+alt+backspace) (save your work first!)
-Go back into Language support and make sure Korean is ticked
-At the bottom there is a box that says "Enable support to enter complex characters" Tick that
-Reload X again 
-Now you should be able to type Korean after you press ctrl+spacebar to change the input language

Thats how I did it, so it should work for you too I think

---

### Post by linuxnewbie999 on 2008-03-20
I followed your steps but it just not working....

---

### Post by ryukent on 2008-03-20
What locale are you using?? Type "locale" in the terminal and look for the line LANG=

If you are not using en_US, you might need to add it into your global file.

---

### Post by linuxnewbie999 on 2008-03-21
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

this is my locale. is all en_US. How do i add korean and chinese language to it?

---

### Post by ryukent on 2008-03-21
Well, if you've already added those languages in the language support section above, then it should be installed. Open a terminal and try:

im-switch -z en_US -s scim

Now reboot. When you get back into ubuntu, open the text editor. It should default to using SCIM as the input method. You'll see a extra toolbar in the top right of your screen. You can switch it to pinyin input mode etc. If you can't see it, try right clicking in the text editor (gedit) and selecting Input Methods / SCIM.

Good luck. If all this fails, you can always use UIM instead. Please see my guide for installing uim for Japanese: [http://ubuntuforums.org/showthread.php?t=684469](http://ubuntuforums.org/showthread.php?t=684469)
You will need to add uim-pinyin and uim-hangul for chinese and korean though.

---

### Post by Kiri on 2008-03-21
Is this in your i18n file?
Try to add the following lines to your i18n file (should be in /etc/sysconfig):

GTK_IM_MODULE=scim
QT_IM_MODULE=scim
XIM_PROGRAM="scim -d"
XMODIFIERS=@im=SCIM

---

### Post by ryukent on 2008-03-21
The im-switch command above should set those environment variables without the need to edit the i18n file.

---

### Post by linuxnewbie999 on 2008-03-21
&#44048;&#49324;&#54632;&#45768;&#45796;. &#35874;&#35874;&#12290;Thank you. It works now. But I cannot right click here to select input method. So I type this in text editor. Why I cannot select scim here?  nyukent, i typed the command but it doesn't work... i need to select input method everytime.. How do i set scim as default input method for all application?

---

### Post by ryukent on 2008-03-21
Maybe im-switch isn't installed. Try running:

sudo apt-get install im-switch

Could you give me the output you get after trying that and running the im-switch -z en_US -s scim command again. Also, did you reboot after that???

---

### Post by linuxnewbie999 on 2008-03-21
nope. I still cannot use scim here.

---

### Post by ryukent on 2008-03-22
Hmm... ok, could you type "export" in the terminal and paste the conents here please. We need to check those environment variables.

---

### Post by ryukent on 2008-03-22
That might be easiest done by entering

export >> export.txt

Then opening the new export.txt file in a text editor so you can copy and paste the whole lot.

---

### Post by linuxnewbie999 on 2008-03-23
There you are the export. 
```

declare -x COLORTERM="gnome-terminal"
declare -x DBUS_SESSION_BUS_ADDRESS="unix:abstract=/tmp/dbus-DrLmusx9eL,guid=67b569b94941cc37936d0d0047e5cf6b"
declare -x DESKTOP_SESSION="default"
declare -x DISPLAY=":0.0"
declare -x GDMSESSION="default"
declare -x GDM_LANG="en_US.UTF-8"
declare -x GDM_XSERVER_LOCATION="local"
declare -x GNOME_DESKTOP_SESSION_ID="Default"
declare -x GNOME_KEYRING_PID="5767"
declare -x GNOME_KEYRING_SOCKET="/tmp/keyring-SKyxCU/socket"
declare -x GTK_IM_MODULE="xim"
declare -x GTK_RC_FILES="/etc/gtk/gtkrc:/home/cff32rd32/.gtkrc-1.2-gnome2"
declare -x HISTCONTROL="ignoreboth"
declare -x HOME="/home/cff32rd32"
declare -x LANG="en_US.UTF-8"
declare -x LESSCLOSE="/usr/bin/lesspipe %s %s"
declare -x LESSOPEN="| /usr/bin/lesspipe %s"
declare -x LOGNAME="cff32rd32"
declare -x LS_COLORS="no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:"
declare -x OLDPWD
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
declare -x PWD="/home/cff32rd32"
declare -x QT_IM_MODULE="xim"
declare -x SESSION_MANAGER="local/cff32rd32-ubuntu:/tmp/.ICE-unix/5770"
declare -x SHELL="/bin/bash"
declare -x SHLVL="1"
declare -x SSH_AGENT_PID="5810"
declare -x SSH_AUTH_SOCK="/tmp/ssh-QGEATL5770/agent.5770"
declare -x TERM="xterm"
declare -x USER="cff32rd32"
declare -x USERNAME="cff32rd32"
declare -x WINDOWID="73400416"
declare -x WINDOWPATH="7"
declare -x XAUTHORITY="/home/cff32rd32/.Xauthority"
declare -x XDG_DATA_DIRS="/usr/local/share/:/usr/share/:/usr/share/gdm/"
declare -x XDG_SESSION_COOKIE="c5b9882c32addacf0fc6820047da3900-1206243175.560850-2056671947"
declare -x XMODIFIERS="@imSCIM"
declare -x http_proxy="http://:8080/"
declare -x no_proxy="localhost,127.0.0.0/8,*.local"

```

---

### Post by ryukent on 2008-03-23
OK it seems like the variables:

GTK_IM_MODULE="xim"
QT_IM_MODULE="xim"
XMODIFIERS="@imSCIM"

have been set somewhere. There's an error in the XMODIFIERS line and it seems XIM mode isn't working for you. The problem is, I have no way of knowing where these are being set because it's likely that they are left over from a failed install your tried. The default installation would not have set the variables this way.

Did you ever create a file that and put these lines in??? Perhaps following a guide somewhere. If so, you need to delete that file, or remove the offending lines.

In the mean time, as long as you installed im-switch, you should be able to override these without doing anything too permanent to your system. First go to the ".xinput.d/" directory in your home directory. It's hidden so you'll need to turn show hidden on. Now delete whatever files are in there and add a new one called
"all_ALL". This should be run whatever locale you are using by the im-switch script which runs at startup.

In the file, paste the lines

GTK_IM_MODULE=scim
QT_IM_MODULE=scim
XIM_PROGRAM="scim -d"
XMODIFIERS=@im=SCIM

Save it and reboot. Hopefully, this will then set the variables correctly for you. If however you've put the previous stuff to run after im-switch, it might overwrite these settings with the old ones. In that case you will need to know where they are being set. Try this though as it should set your default input to SCIM.

---

### Post by seshomaru samma on 2008-03-23
Please notice that the im-switch has been discontinued since fesity
this mean that in the latest version of ubuntu -gutsy you should do this :

 install scim-bridge
```
sudo apt-get install scim-bridge
```
then configure ubuntu to use it by editing the scim file
```
sudo gedit /etc/X11/xinit/xinput.d/scim
```
change the line:
```
GTK_IM_MODULE=xim
```
into :
```
GTK_IM_MODULE="scim-bridge"
```
and restart the computer

SCIM will become the default input system even in an English session

---

### Post by linuxnewbie999 on 2008-03-24
Thank you Ryukent and shesomaru now my scim working perfectly.

---

### Post by ryukent on 2008-03-24
Seshomaru&#27096;,

im-switch has not been discontinued. It's still very much alive in Gutsy and Hardy. It represents a far easier way to adjust the input method on a user or system basis. It sets up the environment variables automatically without the need to edit custom files and makes it far easier to undo the changes too. It also stops conflicts occurring in the future if more than one input method are installed.

---

### Post by seshomaru samma on 2008-03-25
> im-switch has not been discontinued. It's still very much alive in Gutsy and Hardy. It represents a far easier way to adjust the input method on a user or system basis. It sets up the environment variables automatically without the need to edit custom files and makes it far easier to undo the changes too. It also stops conflicts occurring in the future if more than one input method are installed.

I didn't know that. I have used the im-switch on Sidux and Debian but in Gutsy I followed [this]("https://help.ubuntu.com/community/SCIM") which makes no mention of the im-switch and it usually works.

---

### Post by linuxnewbie999 on 2008-04-19
How to make it work in FreeBSD OS?

 in FreeBSD this is my locale file 
```

LANG=
LC_CTYPE="C"
LC_COLLATE="C"
LC_TIME="C"
LC_NUMERIC="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_ALL=


```

and this is .scim/config  file
```

/DefaultIMEngineFactory/~other = d75857a5-4148-4745-89e2-1da7ddaf70a9
/FrontEnd/ChangeFactoryGlobally = false
/FrontEnd/OnTheSpot = true
/FrontEnd/Socket/ConfigReadOnly = false
/FrontEnd/Socket/MaxClients = 512
/FrontEnd/X11/BrokenWchar = true
/FrontEnd/X11/Dynamic = false
/FrontEnd/X11/OnTheSpot = true
/FrontEnd/X11/ServerName = SCIM
/Hotkeys/FrontEnd/NextFactory = Control+Alt+Down,Shift+Control+KeyRelease+Shift_L,Shift+Control+KeyRelease+Shift_R
/Hotkeys/FrontEnd/PreviousFactory = Control+Alt+Up,Shift+Control+KeyRelease+Control_L,Shift+Control+KeyRelease+Control_R
/Hotkeys/FrontEnd/ShowFactoryMenu = Control+Alt+Right
/Hotkeys/FrontEnd/Trigger = Control+space
/Hotkeys/FrontEnd/ValidKeyMask = Shift+Control+Alt+CapsLock+Meta+QuirkKanaRo
/IMEngine/Hangul/CommitByWord = false
/IMEngine/Hangul/HangulKey = Alt+Alt_R+KeyRelease
/IMEngine/Hangul/HanjaKey = Hangul_Hanja,F9
/IMEngine/Hangul/HanjaModeKey = 
/IMEngine/Hangul/KeyboardLayout = 2
/IMEngine/Hangul/ShowCandidateComment = true
/IMEngine/Hangul/UseAsciiMode = false
/IMEngine/RawCode/Locales = default
/IMEngine/Table/AddPhraseKey = Control+a,Control+equal
/IMEngine/Table/DeletePhraseKey = Control+d,Control+minus
/IMEngine/Table/FullWidthLetterKey = Shift+space
/IMEngine/Table/FullWidthPunctKey = Control+period
/IMEngine/Table/LongPhraseFirst = false
/IMEngine/Table/ModeSwitchKey = Alt+Shift_L+KeyRelease,Alt+Shift_R+KeyRelease,Shift+Shift_L+KeyRelease,Shift+Shift_R+KeyRelease
/IMEngine/Table/ShowKeyHint = true
/IMEngine/Table/ShowPrompt = true
/IMEngine/Table/UserPhraseFirst = false
/IMEngine/Table/UserTableBinary = false
/Panel/Gtk/Color/ActiveBackground = light sky blue
/Panel/Gtk/Color/ActiveText = black
/Panel/Gtk/Color/NormalBackground = #F7F3F7
/Panel/Gtk/Color/NormalText = black
/Panel/Gtk/DefaultSticked = false
/Panel/Gtk/Font = default
/Panel/Gtk/LookupTableEmbedded = true
/Panel/Gtk/LookupTableVertical = false
/Panel/Gtk/ShowStatusBox = false
/Panel/Gtk/ShowTrayIcon = true
/Panel/Gtk/ToolBar/AlwaysShow = false
/Panel/Gtk/ToolBar/AutoSnap = true
/Panel/Gtk/ToolBar/HideTimeout = 2
/Panel/Gtk/ToolBar/POS_X = -1
/Panel/Gtk/ToolBar/POS_Y = -1
/Panel/Gtk/ToolBar/ShowFactoryIcon = true
/Panel/Gtk/ToolBar/ShowFactoryName = true
/Panel/Gtk/ToolBar/ShowHelpIcon = true
/Panel/Gtk/ToolBar/ShowMenuIcon = true
/Panel/Gtk/ToolBar/ShowSetupIcon = true
/Panel/Gtk/ToolBar/ShowStickIcon = false
/UpdateTimeStamp = 1208607034:470716


```
I would like to run scim in any fields.

---

### Post by seshomaru samma on 2008-04-19
can't help you with free-BSD
but here is my scim.config:

```
/DefaultIMEngineFactory/en_US = 05235cfc-43ce-490c-b1b1-c5a2185276ae
/DefaultIMEngineFactory/zh_CN = 05235cfc-43ce-490c-b1b1-c5a2185276ae
/FrontEnd/ChangeFactoryGlobally = false
/FrontEnd/IMOpenedByDefault = true
/FrontEnd/OnTheSpot = true
/FrontEnd/SharedInputMethod = true
/FrontEnd/Socket/ConfigReadOnly = false
/FrontEnd/Socket/MaxClients = 512
/FrontEnd/X11/BrokenWchar = true
/FrontEnd/X11/Dynamic = false
/FrontEnd/X11/OnTheSpot = true
/FrontEnd/X11/ServerName = SCIM
/Hotkeys/FrontEnd/NextFactory = Control+Alt+Down,Shift+Control+KeyRelease+Shift_L,Shift+Control+KeyRelease+Shift_R
/Hotkeys/FrontEnd/PreviousFactory = Control+Alt+Up,Shift+Control+KeyRelease+Control_L,Shift+Control+KeyRelease+Control_R
/Hotkeys/FrontEnd/ShowFactoryMenu = Control+Alt+Right
/Hotkeys/FrontEnd/Trigger = Control+space,Shift+space,Zenkaku_Hankaku,Hangul
/Hotkeys/FrontEnd/ValidKeyMask = Shift+Control+Alt+CapsLock+Meta
/IMEngine/Pinyin/ShuangPin = false
/IMEngine/Pinyin/ShuangPinScheme = 0
/IMEngine/RawCode/Locales = default
/Panel/Gtk/Color/ActiveBackground = light sky blue
/Panel/Gtk/Color/ActiveText = black
/Panel/Gtk/Color/NormalBackground = #F7F3F7
/Panel/Gtk/Color/NormalText = black
/Panel/Gtk/DefaultSticked = false
/Panel/Gtk/Font = default
/Panel/Gtk/LookupTableEmbedded = true
/Panel/Gtk/LookupTableVertical = false
/Panel/Gtk/ShowStatusBox = false
/Panel/Gtk/ShowTrayIcon = true
/Panel/Gtk/ToolBar/AlwaysShow = false
/Panel/Gtk/ToolBar/AutoSnap = true
/Panel/Gtk/ToolBar/HideTimeout = 2
/Panel/Gtk/ToolBar/POS_X = 1057
/Panel/Gtk/ToolBar/POS_Y = 895
/Panel/Gtk/ToolBar/ShowFactoryIcon = true
/Panel/Gtk/ToolBar/ShowFactoryName = true
/Panel/Gtk/ToolBar/ShowHelpIcon = true
/Panel/Gtk/ToolBar/ShowMenuIcon = true
/Panel/Gtk/ToolBar/ShowSetupIcon = true
/Panel/Gtk/ToolBar/ShowStickIcon = true
/UpdateTimeStamp = 1208532624:561755
```

my locale:

```
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```

if I remember correctly you can't have C as your locale if you want SCIM to work, you need to set as en_US.UTF-8 or something similar. Better check out the scim website.

---

