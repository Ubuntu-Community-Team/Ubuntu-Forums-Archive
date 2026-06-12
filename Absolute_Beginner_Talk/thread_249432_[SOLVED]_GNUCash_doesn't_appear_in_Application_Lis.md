---
title: "[SOLVED] GNUCash doesn't appear in Application List"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by altonbr on 2006-09-02
I can run 'gnucash' by typing exactly that into the terminal, but it's not on the Applications list.. how do I fix this?

---

### Post by TFX360 on 2006-09-02
> **altonbr said:**
> I can run 'gnucash' by typing exactly that into the terminal, but it's not on the Applications list.. how do I fix this?

Dear altonbr,


You can add it via:

```
Applications/Accessoires/Alacarte Menu Editor
```

Byebye

---

### Post by altonbr on 2006-09-02
I'll remember that next time...

1. It's Applications > System Tools > Applications Menu Editor
2. I think a better (by being more informative) answer would have been to tell me to open the menu editor, click "New Entry" and enter in

```

Name: "Gnucash"
Comment: "Accounting software"
Command: "gnucash"

```

Thanks though.

---

### Post by TFX360 on 2006-09-03
> **altonbr said:**
> I'll remember that next time...

1. It's Applications > System Tools > Applications Menu Editor
2. I think a better (by being more informative) answer would have been to tell me to open the menu editor, click "New Entry" and enter in

```

Name: "Gnucash"
Comment: "Accounting software"
Command: "gnucash"

```

Thanks though.

Well I never did it myself. Thanks for the feedback. You can always install Debian menu


```
aptitude install menu
```

---

### Post by Corvair on 2006-09-05
Hi,
I had the same problem so I went to terminal and ran gnucash from there.

I just added gnucash to applications munu like you suggested but when I click on the menu it will not launch. So there is something else missing, like the command in the propper file.

Can you help?

---

### Post by Linux Lover on 2006-09-05
$ update-menus

Hope this will serve your purpose. :-)

---

### Post by Corvair on 2006-09-05
Updating the menus does not work

---

### Post by altonbr on 2006-09-05
> **Corvair said:**
> Hi,
I had the same problem so I went to terminal and ran gnucash from there.

I just added gnucash to applications munu like you suggested but when I click on the menu it will not launch. So there is something else missing, like the command in the propper file.

Can you help?

If you can run gnucash from the terminal, then make sure whatever you type in 'Command', matches what you would type in the terminal.

Example:

```
$ gnucash
```


@Linux Lover

I've never heard of 'update-menus'

---

### Post by Corvair on 2006-09-05
In A la carte menu editor, if I put in gnucash for command, nothing happens.
When I put in sudo gnucash and start from terminal then terminal opens when I launch gnucash and asks for password which I put in and then gnucash launches.
This is not the way to normaly launch an application. When I revert to the proper way with gnucash for command the application does not launch. I think it has to do with the bin files but I don't know how to proceed to add the right information in the text editor.

Anyone can help?

---

### Post by Tomosaur on 2006-09-05
Try using /usr/bin/gnucash as the command to run.

---

### Post by Corvair on 2006-09-05
Tried "usr/bin/gnucash" and this is the message I get

Details: Failed to execute child process "usr/bin/gnucash" (No such file or directory)

---

### Post by Tomosaur on 2006-09-05
Did you insert the leading slash?:
/usr/bin/gnucash

---

### Post by Corvair on 2006-09-05
You are right I forgot the leading slash, but I just tried with the leading slash and there is no response.

---

### Post by Corvair on 2006-09-05
There is no executable command in /usr/bin/  for gnucash.

How can this be corrected? 

I have removed gnucash completely and reinstalled it but it remains the same.

---

### Post by Linux Lover on 2006-09-06
> **altonbr said:**
> 


@Linux Lover

I've never heard of 'update-menus'

update-menus works on debian. not sure, whether will work on ubuntu or not. i am sorry if it spoil the thread, but my intention was only to give a light to the person suffering problem. Hope all u understand.

---

### Post by Tomosaur on 2006-09-06
> **Corvair said:**
> There is no executable command in /usr/bin/  for gnucash.

How can this be corrected? 

I have removed gnucash completely and reinstalled it but it remains the same.

Try the following steps:
```

dpkg -L gnucash | grep gnucash$

```

This will display a list of possibilities for where the gnucash binary resides. Mine looks like this:
```

/usr/lib/gnucash
/usr/lib/gnucash/gnucash
/usr/lib/gnucash/overrides/gnucash
/usr/bin/gnucash
/usr/share/doc/gnucash
/usr/share/menu/gnucash
/etc/gnucash

```

Scrutinise it carefully. Some of these will be directories. I know that my binary is /usr/bin/gnucash, but it sounds like yours may be elsewhere. Regardless, if none of these work, then gnucash is not installed properly.

---

### Post by Corvair on 2006-09-06
Hello Tomosaur and everyone else.

This is what I got with the command you gave me. I don't know if you can make somthing out of this. If you can let me know what I should change.



/usr/lib/gnucash/libgncmodule.so.0.0.0
/usr/lib/gnucash/libgncmodule.la
/usr/lib/gnucash/gnucash
/usr/lib/gnucash/gnucash/libgw-gnc-module.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-gnc-module.la
/usr/lib/gnucash/gnucash/libgw-engine.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-engine.la
/usr/lib/gnucash/gnucash/libgw-kvp.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-kvp.la
/usr/lib/gnucash/gnucash/libgncmod-engine.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-engine.la
/usr/lib/gnucash/gnucash/libgncmod-backend-file.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-backend-file.la
/usr/lib/gnucash/gnucash/libgncmod-network-utils.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-network-utils.la
/usr/lib/gnucash/gnucash/libgncmod-calculation.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-calculation.la
/usr/lib/gnucash/gnucash/libgncmod-tax-us.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-tax-us.la
/usr/lib/gnucash/gnucash/libgncmod-app-utils.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-app-utils.la
/usr/lib/gnucash/gnucash/libgw-app-utils.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-app-utils.la
/usr/lib/gnucash/gnucash/libgncmod-gnome-utils.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-gnome-utils.la
/usr/lib/gnucash/gnucash/libgw-gnome-utils.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-gnome-utils.la
/usr/lib/gnucash/gnucash/libgncmod-gnome-search.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-gnome-search.la
/usr/lib/gnucash/gnucash/libgw-gnome-search.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-gnome-search.la
/usr/lib/gnucash/gnucash/libgncmod-app-file.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-app-file.la
/usr/lib/gnucash/gnucash/libgw-app-file.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-app-file.la
/usr/lib/gnucash/gnucash/libgncmod-report-system.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-report-system.la
/usr/lib/gnucash/gnucash/libgncmod-standard-reports.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-standard-reports.la
/usr/lib/gnucash/gnucash/libgncmod-utility-reports.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-utility-reports.la
/usr/lib/gnucash/gnucash/libgncmod-locale-reports-us.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-locale-reports-us.la
/usr/lib/gnucash/gnucash/libgncmod-stylesheets.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-stylesheets.la
/usr/lib/gnucash/gnucash/libgncmod-report-gnome.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-report-gnome.la
/usr/lib/gnucash/gnucash/libgw-report-gnome.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-report-gnome.la
/usr/lib/gnucash/gnucash/libgncmod-register-core.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-register-core.la
/usr/lib/gnucash/gnucash/libgw-register-core.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-register-core.la
/usr/lib/gnucash/gnucash/libgncmod-register-gnome.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-register-gnome.la
/usr/lib/gnucash/gnucash/libgncmod-ledger-core.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-ledger-core.la
/usr/lib/gnucash/gnucash/libgncmod-generic-import.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-generic-import.la
/usr/lib/gnucash/gnucash/libgncmod-binary-import.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-binary-import.la
/usr/lib/gnucash/gnucash/libgw-binary-import.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-binary-import.la
/usr/lib/gnucash/gnucash/libgncmod-qif-import.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-qif-import.la
/usr/lib/gnucash/gnucash/libgncmod-ofx.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-ofx.la
/usr/lib/gnucash/gnucash/libgncmod-log-replay.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-log-replay.la
/usr/lib/gnucash/gnucash/libgncmod-business-core.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-business-core.la
/usr/lib/gnucash/gnucash/libgw-business-core.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-business-core.la
/usr/lib/gnucash/gnucash/libgncmod-business-backend-file.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-business-backend-file.la
/usr/lib/gnucash/gnucash/libgncmod-business-utils.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-business-utils.la
/usr/lib/gnucash/gnucash/libgncmod-dialog-tax-table.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-dialog-tax-table.la
/usr/lib/gnucash/gnucash/libgw-dialog-tax-table.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-dialog-tax-table.la
/usr/lib/gnucash/gnucash/libgnc-business-ledger.so.0.0.0
/usr/lib/gnucash/gnucash/libgnc-business-ledger.la
/usr/lib/gnucash/gnucash/libgncmod-business-gnome.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-business-gnome.la
/usr/lib/gnucash/gnucash/libgw-business-gnome.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-business-gnome.la
/usr/lib/gnucash/overrides
/usr/lib/gnucash/overrides/gnucash
/usr/lib/gnucash/overrides/gnucash-env
/usr/lib/gnucash/overrides/gnucash-make-guids
/usr/lib/gnucash/overrides/gnucash-run-script
/usr/lib/gnucash/overrides/guile
/usr/lib/gnucash/libgnc-app-file-gnome.so.0.0.0
/usr/lib/gnucash/libgnc-app-file-gnome.la
/usr/lib/gnucash/libgncgnome.so.0.0.0
/usr/lib/gnucash/libgncgnome.la
/usr/lib/gnucash/libgw-gnc.so.0.0.0
/usr/lib/gnucash/libgw-gnc.la
/usr/bin
/usr/bin/dump-finance-quote
/usr/bin/gnc-prices
/usr/bin/gnucash
/usr/bin/gnucash-env
/usr/bin/gnucash-run-script
/usr/bin/gnucash-make-guids
/usr/bin/gnc-test-env
/usr/bin/gnucash-config
/usr/share
/usr/share/doc
/usr/share/doc/gnucash
/usr/share/doc/gnucash/examples
/usr/share/doc/gnucash/examples/currency.xac
/usr/share/doc/gnucash/examples/taxreport.xac.gz
/usr/share/doc/gnucash/examples/splitdemo.xac
/usr/share/doc/gnucash/examples/trading2.xac.gz
/usr/share/doc/gnucash/examples/test.xac
/usr/share/doc/gnucash/examples/test2.xac
/usr/share/doc/gnucash/examples/test3.xac
/usr/share/doc/gnucash/examples/test4.xac
/usr/share/doc/gnucash/examples/trading.xac
/usr/share/doc/gnucash/examples/xfer.xac
/usr/share/doc/gnucash/examples/currency_tree_xml.xac.gz
/usr/share/doc/gnucash/NEWS.gz
/usr/share/doc/gnucash/changelog.Debian.gz
/usr/share/doc/gnucash/TODO
/usr/share/doc/gnucash/README.Debian
/usr/share/doc/gnucash/copyright
/usr/share/doc/gnucash/changelog.gz
/usr/share/doc/gnucash/AUTHORS.gz
/usr/share/doc/gnucash/README.gz
/usr/share/menu
/usr/share/menu/gnucash
/etc
/etc/gnucash
/etc/gnucash/config
/usr/lib/gnucash/libcore-utils.so.0
/usr/lib/gnucash/libcore-utils.so
/usr/lib/gnucash/libgw-core-utils.so.0
/usr/lib/gnucash/libgw-core-utils.so
/usr/lib/gnucash/libgncmodule.so.0
/usr/lib/gnucash/libgncmodule.so
/usr/lib/gnucash/gnucash/libgw-gnc-module.so.0
/usr/lib/gnucash/gnucash/libgw-gnc-module.so
/usr/lib/gnucash/gnucash/libgw-engine.so.0
/usr/lib/gnucash/gnucash/libgw-engine.so
/usr/lib/gnucash/gnucash/libgw-kvp.so.0
/usr/lib/gnucash/gnucash/libgw-kvp.so
/usr/lib/gnucash/gnucash/libgncmod-engine.so.0
/usr/lib/gnucash/gnucash/libgncmod-engine.so
/usr/lib/gnucash/gnucash/libgncmod-backend-file.so.0
/usr/lib/gnucash/gnucash/libgncmod-backend-file.so
/usr/lib/gnucash/gnucash/libgncmod-network-utils.so.0
/usr/lib/gnucash/gnucash/libgncmod-network-utils.so
/usr/lib/gnucash/gnucash/libgncmod-calculation.so.0
/usr/lib/gnucash/gnucash/libgncmod-calculation.so
/usr/lib/gnucash/gnucash/libgncmod-tax-us.so.0
/usr/lib/gnucash/gnucash/libgncmod-tax-us.so
/usr/lib/gnucash/gnucash/libgncmod-app-utils.so.0
/usr/lib/gnucash/gnucash/libgncmod-app-utils.so
/usr/lib/gnucash/gnucash/libgw-app-utils.so.0
/usr/lib/gnucash/gnucash/libgw-app-utils.so
/usr/lib/gnucash/gnucash/libgncmod-gnome-utils.so.0
/usr/lib/gnucash/gnucash/libgncmod-gnome-utils.so
/usr/lib/gnucash/gnucash/libgw-gnome-utils.so.0
/usr/lib/gnucash/gnucash/libgw-gnome-utils.so
/usr/lib/gnucash/gnucash/libgncmod-gnome-search.so.0
/usr/lib/gnucash/gnucash/libgncmod-gnome-search.so
/usr/lib/gnucash/gnucash/libgw-gnome-search.so.0
/usr/lib/gnucash/gnucash/libgw-gnome-search.so
/usr/lib/gnucash/gnucash/libgncmod-app-file.so.0
/usr/lib/gnucash/gnucash/libgncmod-app-file.so
/usr/lib/gnucash/gnucash/libgw-app-file.so.0
/usr/lib/gnucash/gnucash/libgw-app-file.so
/usr/lib/gnucash/gnucash/libgncmod-report-system.so.0
/usr/lib/gnucash/gnucash/libgncmod-report-system.so
/usr/lib/gnucash/gnucash/libgncmod-standard-reports.so.0
/usr/lib/gnucash/gnucash/libgncmod-standard-reports.so
/usr/lib/gnucash/gnucash/libgncmod-utility-reports.so.0
/usr/lib/gnucash/gnucash/libgncmod-utility-reports.so
/usr/lib/gnucash/gnucash/libgncmod-locale-reports-us.so.0
/usr/lib/gnucash/gnucash/libgncmod-locale-reports-us.so
/usr/lib/gnucash/gnucash/libgncmod-stylesheets.so.0
/usr/lib/gnucash/gnucash/libgncmod-stylesheets.so
/usr/lib/gnucash/gnucash/libgncmod-report-gnome.so.0
/usr/lib/gnucash/gnucash/libgncmod-report-gnome.so
/usr/lib/gnucash/gnucash/libgw-report-gnome.so.0
/usr/lib/gnucash/gnucash/libgw-report-gnome.so
/usr/lib/gnucash/gnucash/libgncmod-register-core.so.0
/usr/lib/gnucash/gnucash/libgncmod-register-core.so
/usr/lib/gnucash/gnucash/libgw-register-core.so.0
/usr/lib/gnucash/gnucash/libgw-register-core.so
/usr/lib/gnucash/gnucash/libgncmod-register-gnome.so.0
/usr/lib/gnucash/gnucash/libgncmod-register-gnome.so
/usr/lib/gnucash/gnucash/libgncmod-ledger-core.so.0
/usr/lib/gnucash/gnucash/libgncmod-ledger-core.so
/usr/lib/gnucash/gnucash/libgncmod-generic-import.so.0
/usr/lib/gnucash/gnucash/libgncmod-generic-import.so
/usr/lib/gnucash/gnucash/libgncmod-binary-import.so.0
/usr/lib/gnucash/gnucash/libgncmod-binary-import.so
/usr/lib/gnucash/gnucash/libgw-binary-import.so.0
/usr/lib/gnucash/gnucash/libgncmod-ofx.so
/usr/lib/gnucash/gnucash/libgw-binary-import.so
/usr/lib/gnucash/gnucash/libgncmod-qif-import.so.0
/usr/lib/gnucash/gnucash/libgncmod-qif-import.so
/usr/lib/gnucash/gnucash/libgncmod-ofx.so.0
/usr/lib/gnucash/gnucash/libgncmod-log-replay.so.0
/usr/lib/gnucash/gnucash/libgncmod-log-replay.so
/usr/lib/gnucash/gnucash/libgncmod-business-core.so.0
/usr/lib/gnucash/gnucash/libgncmod-business-core.so
/usr/lib/gnucash/gnucash/libgw-business-core.so.0
/usr/lib/gnucash/gnucash/libgw-business-core.so
/usr/lib/gnucash/gnucash/libgncmod-business-backend-file.so.0
/usr/lib/gnucash/gnucash/libgncmod-business-backend-file.so
/usr/lib/gnucash/gnucash/libgncmod-business-utils.so.0
/usr/lib/gnucash/gnucash/libgncmod-business-utils.so
/usr/lib/gnucash/gnucash/libgncmod-dialog-tax-table.so.0
/usr/lib/gnucash/gnucash/libgncmod-dialog-tax-table.so
/usr/lib/gnucash/gnucash/libgw-dialog-tax-table.so.0
/usr/lib/gnucash/gnucash/libgw-dialog-tax-table.so
/usr/lib/gnucash/gnucash/libgnc-business-ledger.so.0
/usr/lib/gnucash/gnucash/libgnc-business-ledger.so
/usr/lib/gnucash/gnucash/libgncmod-business-gnome.so.0
/usr/lib/gnucash/gnucash/libgncmod-business-gnome.so
/usr/lib/gnucash/gnucash/libgw-business-gnome.so.0
/usr/lib/gnucash/gnucash/libgw-business-gnome.so
/usr/lib/gnucash/libgnc-app-file-gnome.so.0
/usr/lib/gnucash/libgnc-app-file-gnome.so
/usr/lib/gnucash/libgncgnome.so.0
/usr/lib/gnucash/libgncgnome.so
/usr/lib/gnucash/libgw-gnc.so.0
/usr/lib/gnucash/libgw-gnc.so
/.
/usr
/usr/bin
/usr/bin/rgrep
/usr/share
/usr/share/info
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/grep.1.gz
/usr/share/doc
/usr/share/doc/grep
/usr/share/doc/grep/README
/usr/share/doc/grep/TODO
/usr/share/doc/grep/AUTHORS
/usr/share/doc/grep/THANKS
/usr/share/doc/grep/copyright
/usr/share/doc/grep/changelog.gz
/usr/share/doc/grep/NEWS.gz
/usr/share/doc/grep/changelog.Debian.gz
/bin
/bin/grep
/bin/egrep
/bin/fgrep
/usr/share/man/man1/fgrep.1.gz
/usr/share/man/man1/egrep.1.gz
/usr/share/man/man1/rgrep.1.gz

/.
/usr
/usr/lib
/usr/lib/gnucash
/usr/lib/gnucash/libcore-utils.so.0.0.0
/usr/lib/gnucash/libcore-utils.la
/usr/lib/gnucash/libgw-core-utils.so.0.0.0
/usr/lib/gnucash/libgw-core-utils.la
/usr/lib/gnucash/libgncmodule.so.0.0.0
/usr/lib/gnucash/libgncmodule.la
/usr/lib/gnucash/gnucash
/usr/lib/gnucash/gnucash/libgw-gnc-module.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-gnc-module.la
/usr/lib/gnucash/gnucash/libgw-engine.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-engine.la
/usr/lib/gnucash/gnucash/libgw-kvp.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-kvp.la
/usr/lib/gnucash/gnucash/libgncmod-engine.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-engine.la
/usr/lib/gnucash/gnucash/libgncmod-backend-file.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-backend-file.la
/usr/lib/gnucash/gnucash/libgncmod-network-utils.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-network-utils.la
/usr/lib/gnucash/gnucash/libgncmod-calculation.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-calculation.la
/usr/lib/gnucash/gnucash/libgncmod-tax-us.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-tax-us.la
/usr/lib/gnucash/gnucash/libgncmod-app-utils.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-app-utils.la
/usr/lib/gnucash/gnucash/libgw-app-utils.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-app-utils.la
/usr/lib/gnucash/gnucash/libgncmod-gnome-utils.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-gnome-utils.la
/usr/lib/gnucash/gnucash/libgw-gnome-utils.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-gnome-utils.la
/usr/lib/gnucash/gnucash/libgncmod-gnome-search.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-gnome-search.la
/usr/lib/gnucash/gnucash/libgw-gnome-search.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-gnome-search.la
/usr/lib/gnucash/gnucash/libgncmod-app-file.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-app-file.la
/usr/lib/gnucash/gnucash/libgw-app-file.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-app-file.la
/usr/lib/gnucash/gnucash/libgncmod-report-system.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-report-system.la
/usr/lib/gnucash/gnucash/libgncmod-standard-reports.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-standard-reports.la
/usr/lib/gnucash/gnucash/libgncmod-utility-reports.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-utility-reports.la
/usr/lib/gnucash/gnucash/libgncmod-locale-reports-us.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-locale-reports-us.la
/usr/lib/gnucash/gnucash/libgncmod-stylesheets.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-stylesheets.la
/usr/lib/gnucash/gnucash/libgncmod-report-gnome.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-report-gnome.la
/usr/lib/gnucash/gnucash/libgw-report-gnome.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-report-gnome.la
/usr/lib/gnucash/gnucash/libgncmod-register-core.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-register-core.la
/usr/lib/gnucash/gnucash/libgw-register-core.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-register-core.la
/usr/lib/gnucash/gnucash/libgncmod-register-gnome.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-register-gnome.la
/usr/lib/gnucash/gnucash/libgncmod-ledger-core.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-ledger-core.la
/usr/lib/gnucash/gnucash/libgncmod-generic-import.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-generic-import.la
/usr/lib/gnucash/gnucash/libgncmod-binary-import.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-binary-import.la
/usr/lib/gnucash/gnucash/libgw-binary-import.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-binary-import.la
/usr/lib/gnucash/gnucash/libgncmod-qif-import.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-qif-import.la
/usr/lib/gnucash/gnucash/libgncmod-ofx.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-ofx.la
/usr/lib/gnucash/gnucash/libgncmod-log-replay.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-log-replay.la
/usr/lib/gnucash/gnucash/libgncmod-business-core.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-business-core.la
/usr/lib/gnucash/gnucash/libgw-business-core.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-business-core.la
/usr/lib/gnucash/gnucash/libgncmod-business-backend-file.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-business-backend-file.la
/usr/lib/gnucash/gnucash/libgncmod-business-utils.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-business-utils.la
/usr/lib/gnucash/gnucash/libgncmod-dialog-tax-table.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-dialog-tax-table.la
/usr/lib/gnucash/gnucash/libgw-dialog-tax-table.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-dialog-tax-table.la
/usr/lib/gnucash/gnucash/libgnc-business-ledger.so.0.0.0
/usr/lib/gnucash/gnucash/libgnc-business-ledger.la
/usr/lib/gnucash/gnucash/libgncmod-business-gnome.so.0.0.0
/usr/lib/gnucash/gnucash/libgncmod-business-gnome.la
/usr/lib/gnucash/gnucash/libgw-business-gnome.so.0.0.0
/usr/lib/gnucash/gnucash/libgw-business-gnome.la
/usr/lib/gnucash/overrides
/usr/lib/gnucash/overrides/gnucash
/usr/lib/gnucash/overrides/gnucash-env
/usr/lib/gnucash/overrides/gnucash-make-guids
/usr/lib/gnucash/overrides/gnucash-run-script
/usr/lib/gnucash/overrides/guile
/usr/lib/gnucash/libgnc-app-file-gnome.so.0.0.0
/usr/lib/gnucash/libgnc-app-file-gnome.la
/usr/lib/gnucash/libgncgnome.so.0.0.0
/usr/lib/gnucash/libgncgnome.la
/usr/lib/gnucash/libgw-gnc.so.0.0.0
/usr/lib/gnucash/libgw-gnc.la
/usr/bin
/usr/bin/dump-finance-quote
/usr/bin/gnc-prices
/usr/bin/gnucash
/usr/bin/gnucash-env
/usr/bin/gnucash-run-script
/usr/bin/gnucash-make-guids
/usr/bin/gnc-test-env
/usr/bin/gnucash-config
/usr/share
/usr/share/doc
/usr/share/doc/gnucash
/usr/share/doc/gnucash/examples
/usr/share/doc/gnucash/examples/currency.xac
/usr/share/doc/gnucash/examples/taxreport.xac.gz
/usr/share/doc/gnucash/examples/splitdemo.xac
/usr/share/doc/gnucash/examples/trading2.xac.gz
/usr/share/doc/gnucash/examples/test.xac
/usr/share/doc/gnucash/examples/test2.xac
/usr/share/doc/gnucash/examples/test3.xac
/usr/share/doc/gnucash/examples/test4.xac
/usr/share/doc/gnucash/examples/trading.xac
/usr/share/doc/gnucash/examples/xfer.xac
/usr/share/doc/gnucash/examples/currency_tree_xml.xac.gz
/usr/share/doc/gnucash/NEWS.gz
/usr/share/doc/gnucash/changelog.Debian.gz
/usr/share/doc/gnucash/TODO
/usr/share/doc/gnucash/README.Debian
/usr/share/doc/gnucash/copyright
/usr/share/doc/gnucash/changelog.gz
/usr/share/doc/gnucash/AUTHORS.gz
/usr/share/doc/gnucash/README.gz
/usr/share/menu
/usr/share/menu/gnucash
/etc
/etc/gnucash
/etc/gnucash/config
/usr/lib/gnucash/libcore-utils.so.0
/usr/lib/gnucash/libcore-utils.so
/usr/lib/gnucash/libgw-core-utils.so.0
/usr/lib/gnucash/libgw-core-utils.so
/usr/lib/gnucash/libgncmodule.so.0
/usr/lib/gnucash/libgncmodule.so
/usr/lib/gnucash/gnucash/libgw-gnc-module.so.0
/usr/lib/gnucash/gnucash/libgw-gnc-module.so
/usr/lib/gnucash/gnucash/libgw-engine.so.0
/usr/lib/gnucash/gnucash/libgw-engine.so
/usr/lib/gnucash/gnucash/libgw-kvp.so.0
/usr/lib/gnucash/gnucash/libgw-kvp.so
/usr/lib/gnucash/gnucash/libgncmod-engine.so.0
/usr/lib/gnucash/gnucash/libgncmod-engine.so
/usr/lib/gnucash/gnucash/libgncmod-backend-file.so.0
/usr/lib/gnucash/gnucash/libgncmod-backend-file.so
/usr/lib/gnucash/gnucash/libgncmod-network-utils.so.0
/usr/lib/gnucash/gnucash/libgncmod-network-utils.so
/usr/lib/gnucash/gnucash/libgncmod-calculation.so.0
/usr/lib/gnucash/gnucash/libgncmod-calculation.so
/usr/lib/gnucash/gnucash/libgncmod-tax-us.so.0
/usr/lib/gnucash/gnucash/libgncmod-tax-us.so
/usr/lib/gnucash/gnucash/libgncmod-app-utils.so.0
/usr/lib/gnucash/gnucash/libgncmod-app-utils.so
/usr/lib/gnucash/gnucash/libgw-app-utils.so.0
/usr/lib/gnucash/gnucash/libgw-app-utils.so
/usr/lib/gnucash/gnucash/libgncmod-gnome-utils.so.0
/usr/lib/gnucash/gnucash/libgncmod-gnome-utils.so
/usr/lib/gnucash/gnucash/libgw-gnome-utils.so.0
/usr/lib/gnucash/gnucash/libgw-gnome-utils.so
/usr/lib/gnucash/gnucash/libgncmod-gnome-search.so.0
/usr/lib/gnucash/gnucash/libgncmod-gnome-search.so
/usr/lib/gnucash/gnucash/libgw-gnome-search.so.0
/usr/lib/gnucash/gnucash/libgw-gnome-search.so
/usr/lib/gnucash/gnucash/libgncmod-app-file.so.0
/usr/lib/gnucash/gnucash/libgncmod-app-file.so
/usr/lib/gnucash/gnucash/libgw-app-file.so.0
/usr/lib/gnucash/gnucash/libgw-app-file.so
/usr/lib/gnucash/gnucash/libgncmod-report-system.so.0
/usr/lib/gnucash/gnucash/libgncmod-report-system.so
/usr/lib/gnucash/gnucash/libgncmod-standard-reports.so.0
/usr/lib/gnucash/gnucash/libgncmod-standard-reports.so
/usr/lib/gnucash/gnucash/libgncmod-utility-reports.so.0
/usr/lib/gnucash/gnucash/libgncmod-utility-reports.so
/usr/lib/gnucash/gnucash/libgncmod-locale-reports-us.so.0
/usr/lib/gnucash/gnucash/libgncmod-locale-reports-us.so
/usr/lib/gnucash/gnucash/libgncmod-stylesheets.so.0
/usr/lib/gnucash/gnucash/libgncmod-stylesheets.so
/usr/lib/gnucash/gnucash/libgncmod-report-gnome.so.0
/usr/lib/gnucash/gnucash/libgncmod-report-gnome.so
/usr/lib/gnucash/gnucash/libgw-report-gnome.so.0
/usr/lib/gnucash/gnucash/libgw-report-gnome.so
/usr/lib/gnucash/gnucash/libgncmod-register-core.so.0
/usr/lib/gnucash/gnucash/libgncmod-register-core.so
/usr/lib/gnucash/gnucash/libgw-register-core.so.0
/usr/lib/gnucash/gnucash/libgw-register-core.so
/usr/lib/gnucash/gnucash/libgncmod-register-gnome.so.0
/usr/lib/gnucash/gnucash/libgncmod-register-gnome.so
/usr/lib/gnucash/gnucash/libgncmod-ledger-core.so.0
/usr/lib/gnucash/gnucash/libgncmod-ledger-core.so
/usr/lib/gnucash/gnucash/libgncmod-generic-import.so.0
/usr/lib/gnucash/gnucash/libgncmod-generic-import.so
/usr/lib/gnucash/gnucash/libgncmod-binary-import.so.0
/usr/lib/gnucash/gnucash/libgncmod-binary-import.so
/usr/lib/gnucash/gnucash/libgw-binary-import.so.0
/usr/lib/gnucash/gnucash/libgncmod-ofx.so
/usr/lib/gnucash/gnucash/libgw-binary-import.so
/usr/lib/gnucash/gnucash/libgncmod-qif-import.so.0
/usr/lib/gnucash/gnucash/libgncmod-qif-import.so
/usr/lib/gnucash/gnucash/libgncmod-ofx.so.0
/usr/lib/gnucash/gnucash/libgncmod-log-replay.so.0
/usr/lib/gnucash/gnucash/libgncmod-log-replay.so
/usr/lib/gnucash/gnucash/libgncmod-business-core.so.0
/usr/lib/gnucash/gnucash/libgncmod-business-core.so
/usr/lib/gnucash/gnucash/libgw-business-core.so.0
/usr/lib/gnucash/gnucash/libgw-business-core.so
/usr/lib/gnucash/gnucash/libgncmod-business-backend-file.so.0
/usr/lib/gnucash/gnucash/libgncmod-business-backend-file.so
/usr/lib/gnucash/gnucash/libgncmod-business-utils.so.0
/usr/lib/gnucash/gnucash/libgncmod-business-utils.so
/usr/lib/gnucash/gnucash/libgncmod-dialog-tax-table.so.0
/usr/lib/gnucash/gnucash/libgncmod-dialog-tax-table.so
/usr/lib/gnucash/gnucash/libgw-dialog-tax-table.so.0
/usr/lib/gnucash/gnucash/libgw-dialog-tax-table.so
/usr/lib/gnucash/gnucash/libgnc-business-ledger.so.0
/usr/lib/gnucash/gnucash/libgnc-business-ledger.so
/usr/lib/gnucash/gnucash/libgncmod-business-gnome.so.0
/usr/lib/gnucash/gnucash/libgncmod-business-gnome.so
/usr/lib/gnucash/gnucash/libgw-business-gnome.so.0
/usr/lib/gnucash/gnucash/libgw-business-gnome.so
/usr/lib/gnucash/libgnc-app-file-gnome.so.0
/usr/lib/gnucash/libgnc-app-file-gnome.so
/usr/lib/gnucash/libgncgnome.so.0
/usr/lib/gnucash/libgncgnome.so
/usr/lib/gnucash/libgw-gnc.so.0
/usr/lib/gnucash/libgw-gnc.so
claude@ubuntuClaude:~$

---

### Post by Corvair on 2006-09-06
Here is something else I just downloaded.



claude@ubuntuClaude:~$ sudo dpkg -L gnucash/grep gnucash$
Package `gnucash/grep' is not installed.

Package `gnucash$' is not installed.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

---

### Post by Tomosaur on 2006-09-06
From the looks of it, gnucash is installed to /usr/bin/gnucash

Also, you did the command wrong :P You should copy and paste it exactly as I wrote it, it will strip all the extra stuff which is irrelevant to you from the results.

Seeing as you're still not getting anywhere, type this:
```

export PATH=$PATH:/usr/bin/

```
and then try typing 'gnucash'. If this works, go to your home directory, and add that line to the bottom of the .bashrc file (which is hidden, just type 'nano .bashrc' and it will open for you). Save it, log out, and log back in again.

EDIT: The | is an actual command, it means 'pipe'. What's happening is that dpkg -L is finding everything related to gnucash, and the output is getting sent to grep, which strips away everything else and leaves you with those lines where 'gnucash' is at the end of the line. You cannot interchange it with a slash :P

---

### Post by Corvair on 2006-09-06
Ok, here is the result for the first request


dpkg -L gnucash | grep gnucash$
/usr/lib/gnucash
/usr/lib/gnucash/gnucash
/usr/lib/gnucash/overrides/gnucash
/usr/bin/gnucash
/usr/share/doc/gnucash
/usr/share/menu/gnucash
/etc/gnucash

and the second request...

claude@ubuntuClaude:~$ sudo export PATH=$PATH:/usr/bin/
Password:
sudo: export: command not found
claude@ubuntuClaude:~$


Thanks for your help

---

### Post by Corvair on 2006-09-08
Tomosaur,

I will need more precision on how to proceed.

The export command did not work and as for the other line , I can open the bashrc thing but after that nothing works.
I ad the export PATH=$PATH:/usr/bin/ line at the bottom of that window in the terminal but I cannot save it.
As you can see we are in the absolute biginner  forum so I need foer you to be more pricise

---

