---
title: "Ubuntu Logo in color ASCII art"
date: 2018-02-21
forum: Art &amp; Design
---

### Post by LHammonds on 2018-02-21
Original thread by lemix (2006) - [Ubuntu Ascii Logo Program]("https://ubuntuforums.org/showthread.php?t=295911")
 - A program written in C to create the Ubuntu logo
2nd thread by coralsaw (2007) - [Ubuntu Logo in color ASCII art]("https://ubuntuforums.org/showthread.php?t=351870")
 - An motd file that could be output to the screen

Here is the exact same look to the original logo output from the above posts but using Bash shell script...which could be incorporated into a dynamic motd banner at login.

Color code chart has been included so you can easily swap out the 3 colors with any other colors you want.

logo-color.sh
```

#!/bin/sh
## Black        0;30     Dark Gray     1;30
## Red          0;31     Light Red     1;31
## Green        0;32     Light Green   1;32
## Brown/Orange 0;33     Yellow        1;33
## Blue         0;34     Light Blue    1;34
## Purple       0;35     Light Purple  1;35
## Cyan         0;36     Light Cyan    1;36
## Light Gray   0;37     White         1;37

color1='\033[1;31m'  # light red
color2='\033[1;35m'  # light purple
color3='\033[1;33m'  # light yellow
nocolor='\033[0m'    # no color

printf "               ${color1}.-.${nocolor}\n"
printf "         ${color2}.-'\`\`${color1}(   )${nocolor}\n"
printf "      ${color3},\`\\ ${color2}\\    ${color1}\`-\`${color2}.${nocolor}\n"
printf "     ${color3}/   \\ ${color2}'\`\`-.   \`   ${color3}`lsb_release -s -d`${nocolor}\n"
printf "   ${color2}.-.  ${color3},       ${color2}\`___:  ${nocolor}`uname -srmo`${nocolor}\n"
printf "  ${color2}(   ) ${color3}:       ${color1} ___   ${nocolor}`date`${nocolor}\n"
printf "   ${color2}\`-\`  ${color3}\`      ${color1} ,   :${nocolor}\n"
printf "     ${color3}\\   / ${color1},..-\`   ,${nocolor}\n"
printf "      ${color3}\`./${color1} /    ${color3}.-.${color1}\`${nocolor}\n"
printf "         ${color1}\`-..-${color3}(   )${nocolor}\n"
printf "               ${color3}\`-\`${nocolor}\n"

```

Example output in color from an Ubuntu server:
[IMG]http://hammondslegacy.com/images/linux/Ubuntu-Logo-ASCII.jpg[/IMG]

logo-nocolor.sh
```

#!/bin/sh
printf "               .-.\n"
printf "         .-'\`\`(   )\n"
printf "      ,\`\\ \\    \`-\`.\n"
printf "     /   \\ '\`\`-.   \`   `lsb_release -s -d`\n"
printf "   .-.  ,       \`___:  `uname -srmo`\n"
printf "  (   ) :        ___   `date`\n"
printf "   \`-\`  \`       ,   :\n"
printf "     \\   / ,..-\`   ,\n"
printf "      \`./ /    .-.\`\n"
printf "         \`-..-(   )\n"
printf "               \`-\`\n"

```

Example output from an Ubuntu server.
```

               .-.
         .-'``(   )
      ,`\ \    `-`.
     /   \ '``-.   `   Ubuntu 16.04.3 LTS
   .-.  ,       `___:  Linux 4.4.0-112-generic x86_64 GNU/Linux
  (   ) :        ___   Wed Feb 21 15:38:14 CST 2018
   `-`  `       ,   :
     \   / ,..-`   ,
      `./ /    .-.`
         `-..-(   )
               `-`

```

Extended color example code:
```

#!/bin/sh
## Black        0;30     Dark Gray     1;30
## Red          0;31     Light Red     1;31
## Green        0;32     Light Green   1;32
## Brown/Orange 0;33     Yellow        1;33
## Blue         0;34     Light Blue    1;34
## Purple       0;35     Light Purple  1;35
## Cyan         0;36     Light Cyan    1;36
## Light Gray   0;37     White         1;37

color1='\033[1;31m'    # light red
color2='\033[1;35m'    # light purple
color3='\033[0;33m'    # light yellow
nocolor='\033[0m'      # no color
companyname='\033[1;34mCompany Name\033[0m'
divisionname='\033[1;32mDivision Name\033[0m'

printf "               ${color1}.-.${nocolor}\n"
printf "         ${color2}.-'\`\`${color1}(   )    ${companyname}${nocolor}\n"
printf "      ${color3},\`\\ ${color2}\\    ${color1}\`-\`${color2}.    ${divisionname}${nocolor}\n"
printf "     ${color3}/   \\ ${color2}'\`\`-.   \`   ${color3}`lsb_release -s -d`${nocolor}\n"
printf "   ${color2}.-.  ${color3},       ${color2}\`___:  ${nocolor}`uname -srmo`${nocolor}\n"
printf "  ${color2}(   ) ${color3}:       ${color1} ___   ${nocolor}`date +"%A, %e %B %Y, %r"`${nocolor}\n"
printf "   ${color2}\`-\`  ${color3}\`      ${color1} ,   :${nocolor}  Weather: `curl -s "http://rss.accuweather.com/rss/liveweather_rss.asp?metric=2&locCode=76501" | sed -n '/Currently:/ s/.*: \(.*\): \([0-9]*\)\([CF]\).*/\2°\3, \1/p'`\n"
printf "     ${color3}\\   / ${color1},..-\`   ,${nocolor}   Internal IP: `/sbin/ifconfig ens32 | /bin/grep "inet addr" | /usr/bin/cut -d ":" -f 2 | /usr/bin/cut -d " " -f 1`\n"
printf "      ${color3}\`./${color1} /    ${color3}.-.${color1}\`${nocolor}    External IP: `/usr/bin/wget -q -O - http://icanhazip.com/ | /usr/bin/tail`\n"
printf "         ${color1}\`-..-${color3}(   )${nocolor}    Uptime: `/usr/bin/uptime -p`\n"
printf "               ${color3}\`-\`${nocolor}\n"

```

Extended color example output:
[img]http://hammondslegacy.com/images/linux/Ubuntu-Logo-ASCII2.jpg[/img]

LHammonds

---

### Post by DuckHook on 2018-02-21
This is fantastic! (I'm easily amused.)

Thank you for this.

---

### Post by LHammonds on 2018-02-22
> **DuckHook said:**
> I'm easily amused.LoL, so am I ! ! ! !

I wanted an ASCII art logo for Ubuntu for my SSH login banners and this was the best-looking one I could find.  Couldn't find anything smaller that captured the right "feel" but this works so I stopped looking and did the conversion.

[SIZE=5]Ubuntu Server 16.04 LTS[/SIZE]

**EDIT:** For those that want to know how to use this in your SSH login in version 16.04, here's how:

#1 - Disable the header and help text sections of the current process by removing the execute permission.
```
sudo chmod 644 /etc/update-motd.d/00-header
sudo chmod 644 /etc/update-motd.d/10-help-text
```

#2 - Create a new script that will execute before the remaining scripts (updates available, reboot required, etc.)
```
sudo touch /etc/update-motd.d/01-custom-logo
sudo chmod 755 /etc/update-motd.d/01-custom-logo
sudo chown root:root /etc/update-motd.d/01-custom-logo
```

#3 - Now edit the 01-custom-logo file and copy/paste one of the above examples.

#4 - Make sure it runs how you would expect by executing it
```
/etc/update-motd.d/01-custom-logo
```

#5 - Within 10 minutes your SSH login will display your crispy-new ASCII art

LHammonds

---

### Post by DuckHook on 2018-02-22
Cool.

Will try this out after house guests depart.

---

### Post by LHammonds on 2018-05-03
[SIZE=5]Ubuntu Server 18.04 LTS[/SIZE]

For those that want to know how to use this in your SSH login for version 18.04, here's how:

#1 - Disable the header and help text sections of the current process by removing the execute permission.

```
sudo chmod 644 /etc/update-motd.d/00-header
sudo chmod 644 /etc/update-motd.d/10-help-text
sudo chmod 644 /etc/update-motd.d/50-landscape-sysinfo
sudo chmod 644 /etc/update-motd.d/50-motd-news
sudo chmod 644 /etc/update-motd.d/80-livepatch
```

#2 - Create a new script that will execute before the remaining scripts (updates available, reboot required, etc.)

```
sudo touch /etc/update-motd.d/01-custom-logo
sudo chmod 755 /etc/update-motd.d/01-custom-logo
sudo chown root:root /etc/update-motd.d/01-custom-logo
```

#3 - Now edit the 01-custom-logo file and copy/paste one of the above examples.

NOTE: If you want the Internal IP, the output format changed a bit in 18.04.  Find this line:
```
printf "     ${color3}\\   / ${color1},..-\`   ,${nocolor}   Internal IP: `/sbin/ifconfig ens32 | /bin/grep "inet addr" | /usr/bin/cut -d ":" -f 2 | /usr/bin/cut -d " " -f 1`\n"
```
and change it to:
```
printf "     ${color3}\\   / ${color1},..-\`   ,${nocolor}   Internal IP: `/sbin/ifconfig ens32 | /bin/grep "inet " | /usr/bin/cut -d ":" -f 2 | /usr/bin/cut -d " " -f 10`\n"
```
Assuming your NIC is "ens32" but if not, make sure you change it to your NIC name so it can find it.

#4 - Make sure it runs how you would expect by executing it

```
/etc/update-motd.d/01-custom-logo
```

#5 - Within 10 minutes your SSH login will display your crispy-new ASCII art

---

### Post by joshua_rebeldevil on 2018-07-24
Thank you very much for your efforts and for sharing the updates!

---

### Post by DuckHook on 2019-04-16
On revisiting this cute but excellent tutorial&#8230;

For the benefit of new users, when making LHammonds' above changes, remember to prepend with [FONT=Courier New]sudo[/FONT].

---

### Post by ukstickermarket on 2019-06-20
Cool! Thanks for sharing though. We appreciate this

---

### Post by LHammonds on 2019-07-10
> **DuckHook said:**
> On revisiting this cute but excellent tutorial&#8230;

For the benefit of new users, when making LHammonds' above changes, remember to prepend with [FONT=Courier New]sudo[/FONT].
Whoops, I've updated the posts to include them.

I've also created a clone of this thread on [my forums](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=259) so it exists in more places than one.  ;)

LHammonds

---

### Post by wariswala on 2019-09-23
> **LHammonds said:**
> Original thread by lemix (2006) - [Ubuntu Ascii Logo Program]("https://ubuntuforums.org/showthread.php?t=295911")
 - A program written in C to create the Ubuntu logo
2nd thread by coralsaw (2007) - [Ubuntu Logo in color ASCII art]("https://ubuntuforums.org/showthread.php?t=351870")
 - An motd file that could be output to the screen
[[COLOR=#000000]shillong teer results[/COLOR]]("https://shillongteerresults.in/") provide you all the updates easily.
Here is the exact same look to the original logo output from the above posts but using Bash shell script...which could be incorporated into a dynamic motd banner at login.

Color code chart has been included so you can easily swap out the 3 colors with any other colors you want.

logo-color.sh
```

#!/bin/sh
## Black        0;30     Dark Gray     1;30
## Red          0;31     Light Red     1;31
## Green        0;32     Light Green   1;32
## Brown/Orange 0;33     Yellow        1;33
## Blue         0;34     Light Blue    1;34
## Purple       0;35     Light Purple  1;35
## Cyan         0;36     Light Cyan    1;36
## Light Gray   0;37     White         1;37

color1='\033[1;31m'  # light red
color2='\033[1;35m'  # light purple
color3='\033[1;33m'  # light yellow
nocolor='\033[0m'    # no color

printf "               ${color1}.-.${nocolor}\n"
printf "         ${color2}.-'\`\`${color1}(   )${nocolor}\n"
printf "      ${color3},\`\\ ${color2}\\    ${color1}\`-\`${color2}.${nocolor}\n"
printf "     ${color3}/   \\ ${color2}'\`\`-.   \`   ${color3}`lsb_release -s -d`${nocolor}\n"
printf "   ${color2}.-.  ${color3},       ${color2}\`___:  ${nocolor}`uname -srmo`${nocolor}\n"
printf "  ${color2}(   ) ${color3}:       ${color1} ___   ${nocolor}`date`${nocolor}\n"
printf "   ${color2}\`-\`  ${color3}\`      ${color1} ,   :${nocolor}\n"
printf "     ${color3}\\   / ${color1},..-\`   ,${nocolor}\n"
printf "      ${color3}\`./${color1} /    ${color3}.-.${color1}\`${nocolor}\n"
printf "         ${color1}\`-..-${color3}(   )${nocolor}\n"
printf "               ${color3}\`-\`${nocolor}\n"

```

Example output in color from an Ubuntu server:
[IMG]http://hammondslegacy.com/images/linux/Ubuntu-Logo-ASCII.jpg[/IMG]

logo-nocolor.sh
```

#!/bin/sh
printf "               .-.\n"
printf "         .-'\`\`(   )\n"
printf "      ,\`\\ \\    \`-\`.\n"
printf "     /   \\ '\`\`-.   \`   `lsb_release -s -d`\n"
printf "   .-.  ,       \`___:  `uname -srmo`\n"
printf "  (   ) :        ___   `date`\n"
printf "   \`-\`  \`       ,   :\n"
printf "     \\   / ,..-\`   ,\n"
printf "      \`./ /    .-.\`\n"
printf "         \`-..-(   )\n"
printf "               \`-\`\n"

```

Example output from an Ubuntu server.
```

               .-.
         .-'``(   )
      ,`\ \    `-`.
     /   \ '``-.   `   Ubuntu 16.04.3 LTS
   .-.  ,       `___:  Linux 4.4.0-112-generic x86_64 GNU/Linux
  (   ) :        ___   Wed Feb 21 15:38:14 CST 2018
   `-`  `       ,   :
     \   / ,..-`   ,
      `./ /    .-.`
         `-..-(   )
               `-`

```

Extended color example code:
```

#!/bin/sh
## Black        0;30     Dark Gray     1;30
## Red          0;31     Light Red     1;31
## Green        0;32     Light Green   1;32
## Brown/Orange 0;33     Yellow        1;33
## Blue         0;34     Light Blue    1;34
## Purple       0;35     Light Purple  1;35
## Cyan         0;36     Light Cyan    1;36
## Light Gray   0;37     White         1;37

color1='\033[1;31m'    # light red
color2='\033[1;35m'    # light purple
color3='\033[0;33m'    # light yellow
nocolor='\033[0m'      # no color
companyname='\033[1;34mCompany Name\033[0m'
divisionname='\033[1;32mDivision Name\033[0m'

printf "               ${color1}.-.${nocolor}\n"
printf "         ${color2}.-'\`\`${color1}(   )    ${companyname}${nocolor}\n"
printf "      ${color3},\`\\ ${color2}\\    ${color1}\`-\`${color2}.    ${divisionname}${nocolor}\n"
printf "     ${color3}/   \\ ${color2}'\`\`-.   \`   ${color3}`lsb_release -s -d`${nocolor}\n"
printf "   ${color2}.-.  ${color3},       ${color2}\`___:  ${nocolor}`uname -srmo`${nocolor}\n"
printf "  ${color2}(   ) ${color3}:       ${color1} ___   ${nocolor}`date +"%A, %e %B %Y, %r"`${nocolor}\n"
printf "   ${color2}\`-\`  ${color3}\`      ${color1} ,   :${nocolor}  Weather: `curl -s "http://rss.accuweather.com/rss/liveweather_rss.asp?metric=2&locCode=76501" | sed -n '/Currently:/ s/.*: \(.*\): \([0-9]*\)\([CF]\).*/\2°\3, \1/p'`\n"
printf "     ${color3}\\   / ${color1},..-\`   ,${nocolor}   Internal IP: `/sbin/ifconfig ens32 | /bin/grep "inet addr" | /usr/bin/cut -d ":" -f 2 | /usr/bin/cut -d " " -f 1`\n"
printf "      ${color3}\`./${color1} /    ${color3}.-.${color1}\`${nocolor}    External IP: `/usr/bin/wget -q -O - http://icanhazip.com/ | /usr/bin/tail`\n"
printf "         ${color1}\`-..-${color3}(   )${nocolor}    Uptime: `/usr/bin/uptime -p`\n"
printf "               ${color3}\`-\`${nocolor}\n"

```

Extended color example output:
[IMG]http://hammondslegacy.com/images/linux/Ubuntu-Logo-ASCII2.jpg[/IMG]

LHammonds
Cool One..! I will try to share with you which i have created.

---

### Post by lyleharper on 2019-10-24
> **LHammonds said:**
> Original thread by lemix (2006) - [Ubuntu Ascii Logo Program]("https://ubuntuforums.org/showthread.php?t=295911")
 - A program written in C to create the Ubuntu logo
2nd thread by coralsaw (2007) - [Ubuntu Logo in color ASCII art]("https://ubuntuforums.org/showthread.php?t=351870")
 - An motd file that could be output to the screen

Here is the exact same look to the original logo output from the above posts but using Bash shell script...which could be incorporated into a dynamic motd banner at login.

Color code chart has been included so you can easily swap out the 3 colors with any other colors you want.

logo-color.sh
```

#!/bin/sh
## Black        0;30     Dark Gray     1;30
## Red          0;31     Light Red     1;31
## Green        0;32     Light Green   1;32
## Brown/Orange 0;33     Yellow        1;33
## Blue         0;34     Light Blue    1;34
## Purple       0;35     Light Purple  1;35
## Cyan         0;36     Light Cyan    1;36
## Light Gray   0;37     White         1;37

color1='\033[1;31m'  # light red
color2='\033[1;35m'  # light purple
color3='\033[1;33m'  # light yellow
nocolor='\033[0m'    # no color

printf "               ${color1}.-.${nocolor}\n"
printf "         ${color2}.-'\`\`${color1}(   )${nocolor}\n"
printf "      ${color3},\`\\ ${color2}\\    ${color1}\`-\`${color2}.${nocolor}\n"
printf "     ${color3}/   \\ ${color2}'\`\`-.   \`   ${color3}`lsb_release -s -d`${nocolor}\n"
printf "   ${color2}.-.  ${color3},       ${color2}\`___:  ${nocolor}`uname -srmo`${nocolor}\n"
printf "  ${color2}(   ) ${color3}:       ${color1} ___   ${nocolor}`date`${nocolor}\n"
printf "   ${color2}\`-\`  ${color3}\`      ${color1} ,   :${nocolor}\n"
printf "     ${color3}\\   / ${color1},..-\`   ,${nocolor}\n"
printf "      ${color3}\`./${color1} /    ${color3}.-.${color1}\`${nocolor}\n"
printf "         ${color1}\`-..-${color3}(   )${nocolor}\n"
printf "               ${color3}\`-\`${nocolor}\n"

```

Example output in color from an Ubuntu server:
[IMG]http://hammondslegacy.com/images/linux/Ubuntu-Logo-ASCII.jpg[/IMG]

logo-nocolor.sh
```

#!/bin/sh
printf "               .-.\n"
printf "         .-'\`\`(   )\n"
printf "      ,\`\\ \\    \`-\`.\n"
printf "     /   \\ '\`\`-.   \`   `lsb_release -s -d`\n"
printf "   .-.  ,       \`___:  `uname -srmo`\n"
printf "  (   ) :        ___   `date`\n"
printf "   \`-\`  \`       ,   :\n"
printf "     \\   / ,..-\`   ,\n"
printf "      \`./ /    .-.\`\n"
printf "         \`-..-(   )\n"
printf "               \`-\`\n"

```

Example output from an Ubuntu server.
[[COLOR=#000000]google street view[/COLOR]]("https://ggstreetview.com") of any address or GPS coordinates
```

               .-.
         .-'``(   )
      ,`\ \    `-`.
     /   \ '``-.   `   Ubuntu 16.04.3 LTS
   .-.  ,       `___:  Linux 4.4.0-112-generic x86_64 GNU/Linux
  (   ) :        ___   Wed Feb 21 15:38:14 CST 2018
   `-`  `       ,   :
     \   / ,..-`   ,
      `./ /    .-.`
         `-..-(   )
               `-`

```

Extended color example code:
```

#!/bin/sh
## Black        0;30     Dark Gray     1;30
## Red          0;31     Light Red     1;31
## Green        0;32     Light Green   1;32
## Brown/Orange 0;33     Yellow        1;33
## Blue         0;34     Light Blue    1;34
## Purple       0;35     Light Purple  1;35
## Cyan         0;36     Light Cyan    1;36
## Light Gray   0;37     White         1;37

color1='\033[1;31m'    # light red
color2='\033[1;35m'    # light purple
color3='\033[0;33m'    # light yellow
nocolor='\033[0m'      # no color
companyname='\033[1;34mCompany Name\033[0m'
divisionname='\033[1;32mDivision Name\033[0m'

printf "               ${color1}.-.${nocolor}\n"
printf "         ${color2}.-'\`\`${color1}(   )    ${companyname}${nocolor}\n"
printf "      ${color3},\`\\ ${color2}\\    ${color1}\`-\`${color2}.    ${divisionname}${nocolor}\n"
printf "     ${color3}/   \\ ${color2}'\`\`-.   \`   ${color3}`lsb_release -s -d`${nocolor}\n"
printf "   ${color2}.-.  ${color3},       ${color2}\`___:  ${nocolor}`uname -srmo`${nocolor}\n"
printf "  ${color2}(   ) ${color3}:       ${color1} ___   ${nocolor}`date +"%A, %e %B %Y, %r"`${nocolor}\n"
printf "   ${color2}\`-\`  ${color3}\`      ${color1} ,   :${nocolor}  Weather: `curl -s "http://rss.accuweather.com/rss/liveweather_rss.asp?metric=2&locCode=76501" | sed -n '/Currently:/ s/.*: \(.*\): \([0-9]*\)\([CF]\).*/\2°\3, \1/p'`\n"
printf "     ${color3}\\   / ${color1},..-\`   ,${nocolor}   Internal IP: `/sbin/ifconfig ens32 | /bin/grep "inet addr" | /usr/bin/cut -d ":" -f 2 | /usr/bin/cut -d " " -f 1`\n"
printf "      ${color3}\`./${color1} /    ${color3}.-.${color1}\`${nocolor}    External IP: `/usr/bin/wget -q -O - http://icanhazip.com/ | /usr/bin/tail`\n"
printf "         ${color1}\`-..-${color3}(   )${nocolor}    Uptime: `/usr/bin/uptime -p`\n"
printf "               ${color3}\`-\`${nocolor}\n"

```

Extended color example output:
[IMG]http://hammondslegacy.com/images/linux/Ubuntu-Logo-ASCII2.jpg[/IMG]

LHammonds

Cool. I like it!

---

### Post by leowu12 on 2019-11-26
damm, looks hard

---

### Post by LHammonds on 2020-05-03
[SIZE=5]Ubuntu Server 20.04 LTS[/SIZE]

For those that want to know how to use this in your SSH login for version 20.04, here's how:

#1 - Disable the header and help text sections of the current process by removing the execute permission.

```
sudo chmod 644 /etc/update-motd.d/00-header
sudo chmod 644 /etc/update-motd.d/10-help-text
sudo chmod 644 /etc/update-motd.d/50-landscape-sysinfo
sudo chmod 644 /etc/update-motd.d/50-motd-news

```

#2 - Create a new script that will execute before the remaining scripts (updates available, reboot required, etc.)

```
sudo touch /etc/update-motd.d/01-custom-logo
sudo chmod 755 /etc/update-motd.d/01-custom-logo
sudo chown root:root /etc/update-motd.d/01-custom-logo
```

#3 - Now edit the 01-custom-logo file and copy/paste one of the above examples.

NOTE: If you want the Internal IP, the output format changed a bit in 20.04.  Find this line:
```
printf "     ${color3}\\   / ${color1},..-\`   ,${nocolor}   Internal IP: `/sbin/ifconfig ens32 | /bin/grep "inet addr" | /usr/bin/cut -d ":" -f 2 | /usr/bin/cut -d " " -f 1`\n"
```
and change it to:
```
printf "     ${color3}\\   / ${color1},..-\`   ,${nocolor}   Internal IP: `/usr/sbin/ip -4 address show ens32 | /usr/bin/grep inet | /usr/bin/cut -d ' ' -f 6`\n"
```
Assuming your NIC is "ens32" but if not, make sure you change it to your NIC name so it can find it.

#4 - Make sure it runs how you would expect by executing it

```
/etc/update-motd.d/01-custom-logo
```

#5 - Within 10 minutes your SSH login will display your crispy-new ASCII art

---

