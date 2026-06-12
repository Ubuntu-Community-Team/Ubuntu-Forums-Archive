---
title: "CreateTorrent @ Problems"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by morphineinduced on 2006-04-23
No its not a silly question ....... yes I downloaded it after I got it off the site .... I normally do this with AZ but I am tired of running java ..... now the thing is , I have only used the url that I normally use to upload to that site ..... infact to be honest with you I have never heard of anything being called a external torrent before I tried this ..... I am not all knowing .... so maybe this is something I am expected to know at this point in time but I dont know it .....

now this is what the directions are for that program I used to make that torrent ...

createtorrent [OPTIONS] -a announce inputfile/directory output

This will create a bittorrent file from the given inputfile or the files of the given directory with the announce url announce:6881/announce. The output is written to the file output. The following additional options exist:
--announce -a announceurl sets the announce url
--port -p port sets the port of the tracker, default: 6881
--path -t path sets the path on the server, default: /announce
--piecelength -l piecelen sets the piece length in bytes, default: 262144
--comment -c comment adds an optional comment to the torrent file
--version -v version of createtorrent
--help -h this help screen



Now this is just a example of how I made it

createtorrent -a [http://imanoob.com/announce.php](http://imanoob.com/announce.php) death.rar ~ death.torrent 





Then I did this after someone gave me some advice on using -t and this is what happened when I did it 

this is what happened when I did that command ................


morphineinduced@linux:~> createtorrent -a [http://i](http://i) suck.com/ -t death ~ death.torrent
ignoring /home/morphineinduced/.
ignoring /home/morphineinduced/..
ignoring /home/morphineinduced/.qt
adding /home/morphineinduced/JOB
ignoring /home/morphineinduced/bin
ignoring /home/morphineinduced/.kde
ignoring /home/morphineinduced/.vlc
ignoring /home/morphineinduced/Documents
ignoring /home/morphineinduced/.cddb
adding /home/morphineinduced/.dmrc
adding /home/morphineinduced/.exrc
ignoring /home/morphineinduced/.fvwm
ignoring /home/morphineinduced/.java
ignoring /home/morphineinduced/.mcop
ignoring /home/morphineinduced/.skel
ignoring /home/morphineinduced/.wine
ignoring /home/morphineinduced/.xine
ignoring /home/morphineinduced/.xmms
adding /home/morphineinduced/.y2log-1
adding /home/morphineinduced/.y2log-2
adding /home/morphineinduced/.y2log-3
adding /home/morphineinduced/.y2log-4
adding /home/morphineinduced/.y2log-5
adding /home/morphineinduced/.y2log-6
adding /home/morphineinduced/.y2log-7
adding /home/morphineinduced/.y2log-8
adding /home/morphineinduced/.y2log-9
adding /home/morphineinduced/.bashrc
ignoring /home/morphineinduced/.gnome2_private
adding /home/morphineinduced/death
adding /home/morphineinduced/nitro
ignoring /home/morphineinduced/.clamtk
ignoring /home/morphineinduced/.config
ignoring /home/morphineinduced/.dvdcss
ignoring /home/morphineinduced/.mozilla
ignoring /home/morphineinduced/.gconfd
ignoring /home/morphineinduced/.gnome2
ignoring /home/morphineinduced/.bittorrent
ignoring /home/morphineinduced/.gstreamer-0.8
adding /home/morphineinduced/.kermrc
ignoring /home/morphineinduced/.klamav
adding /home/morphineinduced/.realplayerrc
adding /home/morphineinduced/FlashGet1-1.71plus.rar
adding /home/morphineinduced/.xcompmgrrc
adding /home/morphineinduced/.mcoprc
adding /home/morphineinduced/.muttrc
ignoring /home/morphineinduced/.gimp-2.2
adding /home/morphineinduced/.ICEauthority
adding /home/morphineinduced/Silent.Hill.2006.VCD.CAM-SaGa.torrent
ignoring /home/morphineinduced/.nicotine
adding /home/morphineinduced/World_Wind_1.3.4_Full_beta_4.exe
ignoring /home/morphineinduced/public_html
adding /home/morphineinduced/.urlview
adding /home/morphineinduced/death.torrent
ignoring /home/morphineinduced/Desktop
ignoring /home/morphineinduced/.xemacs
adding /home/morphineinduced/.esd_auth
adding /home/morphineinduced/.bash_history
adding /home/morphineinduced/stl18645addn1.jpg
adding /home/morphineinduced/stl18645addn3.jpg
ignoring /home/morphineinduced/.kpackage
ignoring /home/morphineinduced/.avidemux
adding /home/morphineinduced/.gtk_qt_engine_rc
ignoring /home/morphineinduced/.azureus
adding /home/morphineinduced/.DCOPserver_linux_:0
adding /home/morphineinduced/.DCOPserver_linux__0
ignoring /home/morphineinduced/.thumbnails
adding /home/morphineinduced/.Xauthority
adding /home/morphineinduced/.xinitrc.template
adding /home/morphineinduced/.profile
adding /home/morphineinduced/.recently-used
adding /home/morphineinduced/.xcoralrc
ignoring /home/morphineinduced/.xdg_menu_cache
adding /home/morphineinduced/.ispell_english
adding /home/morphineinduced/.windows-label
adding /home/morphineinduced/.emacs
ignoring /home/morphineinduced/.gconf
ignoring /home/morphineinduced/.fonts
ignoring /home/morphineinduced/.gnupg
adding /home/morphineinduced/.kderc
ignoring /home/morphineinduced/.local
adding /home/morphineinduced/.y2log
ignoring /home/morphineinduced/.yast2
adding /home/morphineinduced/Sin_City_MP4_DVDRIP_PSP.torrent
adding /home/morphineinduced/.xim.template
adding /home/morphineinduced/.xtalkrc
ignoring /home/morphineinduced/.macromedia
ignoring /home/morphineinduced/.ooo-2.0-pre
adding /home/morphineinduced/.xsession-errors
ignoring /home/morphineinduced/azureus
adding /home/morphineinduced/.fonts.conf
adding /home/morphineinduced/.dvipsrc
adding /home/morphineinduced/.mailcap
adding /home/morphineinduced/.fonts.cache-1
morphineinduced@linux:~>


that doesnt look right at all



if someone could help .........thanks

---

### Post by JasonL on 2006-04-23
try removing the trailing slash from [http://isuck.com/](http://isuck.com/)

---

### Post by morphineinduced on 2006-04-24
I did that and I got that huge list to still appear .....  I know this program uses as default the port 6881 and I know it needs to be something far from it ......  so if I change it then everything would be all good

---

