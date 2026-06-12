---
title: "Help installing XAMPP"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by ImThatNerd on 2008-04-06
I was following the instructions here: [http://www.apachefriends.org/en/xampp-linux.html#374](http://www.apachefriends.org/en/xampp-linux.html#374)

I downloaded it to my desktop and I run the command and get some errors. 

```
ryan@ryan-desktop:~$ tar xvfz xampp-linux-1.6.6.tar.gz -C /opt
tar: xampp-linux-1.6.6.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
ryan@ryan-desktop:~$ 


```

I am not experienced in terminal at all, so I apologize.

---

### Post by bsharp on 2008-04-06
```
cd Desktop
```

You are in your home directory, and the file is on the desktop, so you need to change to where the file is first.

---

### Post by louieb on 2008-04-06
I've used XAMPP and done a normal Ubuntu lamp install.
The Ubuntu lamp install is easier.
```
sudo tasksel install lamp-server 
```
But for a dev machine XAMPP is ok too. [HOWTO: (XAMPP) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=223410")

More on LAMP  [ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Once either is installed both are about the same trouble to configure. 
But probably get more help (may or may not be better)  if you go with the regular LAMP install.

---

### Post by ImThatNerd on 2008-04-06
Grr I am dumb. I went to that directory and ran the command and only this happened.

```
tory
lampp/share/xampp-control-panel/README
tar: lampp/share/xampp-control-panel/README: Cannot open: No such file or directory
lampp/share/xampp-control-panel/simple-glade-codegen.py
tar: lampp/share/xampp-control-panel/simple-glade-codegen.py: Cannot open: No such file or directory
lampp/share/xampp-control-panel/SimpleGladeApp.py
tar: lampp/share/xampp-control-panel/SimpleGladeApp.py: Cannot open: No such file or directory
lampp/share/xampp-control-panel/SimpleGladeApp.pyc
tar: lampp/share/xampp-control-panel/SimpleGladeApp.pyc: Cannot open: No such file or directory
lampp/share/xampp-control-panel/xampp-control-panel.glade
tar: lampp/share/xampp-control-panel/xampp-control-panel.glade: Cannot open: No such file or directory
lampp/share/xampp-control-panel/xampp-control-panel
tar: lampp/share/xampp-control-panel/xampp-control-panel: Cannot open: No such file or directory
lampp/share/xampp-control-panel/xampp-control-panel.py
tar: lampp/share/xampp-control-panel/xampp-control-panel.py: Cannot open: No such file or directory
lampp/share/gtk-doc/
tar: lampp/share/gtk-doc: Cannot mkdir: No such file or directory
lampp/share/gtk-doc/html/
tar: lampp/share/gtk-doc/html: Cannot mkdir: No such file or directory
lampp/share/gtk-doc/html/libxml2/
tar: lampp/share/gtk-doc/html/libxml2: Cannot mkdir: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2.devhelp
tar: lampp/share/gtk-doc/html/libxml2/libxml2.devhelp: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/home.png
tar: lampp/share/gtk-doc/html/libxml2/home.png: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/left.png
tar: lampp/share/gtk-doc/html/libxml2/left.png: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/right.png
tar: lampp/share/gtk-doc/html/libxml2/right.png: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/up.png
tar: lampp/share/gtk-doc/html/libxml2/up.png: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/style.css
tar: lampp/share/gtk-doc/html/libxml2/style.css: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/index.html
tar: lampp/share/gtk-doc/html/libxml2/index.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/general.html
tar: lampp/share/gtk-doc/html/libxml2/general.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-c14n.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-c14n.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-catalog.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-catalog.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-chvalid.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-chvalid.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-debugXML.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-debugXML.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-dict.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-dict.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-DOCBparser.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-DOCBparser.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-encoding.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-encoding.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-entities.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-entities.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-globals.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-globals.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-hash.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-hash.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-HTMLparser.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-HTMLparser.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-HTMLtree.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-HTMLtree.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-list.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-list.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-nanoftp.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-nanoftp.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-nanohttp.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-nanohttp.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-parser.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-parser.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-parserInternals.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-parserInternals.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-pattern.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-pattern.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-relaxng.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-relaxng.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-SAX2.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-SAX2.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-SAX.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-SAX.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-schemasInternals.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-schemasInternals.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-schematron.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-schematron.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-threads.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-threads.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-tree.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-tree.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-uri.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-uri.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-valid.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-valid.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-xinclude.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-xinclude.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-xlink.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-xlink.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-xmlautomata.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-xmlautomata.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-xmlerror.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-xmlerror.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-xmlexports.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-xmlexports.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-xmlIO.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-xmlIO.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-xmlmemory.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-xmlmemory.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-xmlmodule.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-xmlmodule.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-xmlreader.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-xmlreader.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-xmlregexp.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-xmlregexp.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-xmlsave.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-xmlsave.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-xmlschemas.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-xmlschemas.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-xmlschemastypes.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-xmlschemastypes.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-xmlstring.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-xmlstring.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-xmlunicode.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-xmlunicode.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-xmlversion.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-xmlversion.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-xmlwriter.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-xmlwriter.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-xpath.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-xpath.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-xpathInternals.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-xpathInternals.html: Cannot open: No such file or directory
lampp/share/gtk-doc/html/libxml2/libxml2-xpointer.html
tar: lampp/share/gtk-doc/html/libxml2/libxml2-xpointer.html: Cannot open: No such file or directory
lampp/tmp/
tar: lampp/tmp: Cannot mkdir: No such file or directory
lampp/tmp/eaccelerator/
tar: lampp/tmp/eaccelerator: Cannot mkdir: No such file or directory
lampp/var/
tar: lampp/var: Cannot mkdir: No such file or directory
lampp/var/mysql/
tar: lampp/var/mysql: Cannot mkdir: No such file or directory
lampp/var/mysql/cdcol/
tar: lampp/var/mysql/cdcol: Cannot mkdir: No such file or directory
lampp/var/mysql/cdcol/cds.MYI
tar: lampp/var/mysql/cdcol/cds.MYI: Cannot open: No such file or directory
lampp/var/mysql/cdcol/cds.MYD
tar: lampp/var/mysql/cdcol/cds.MYD: Cannot open: No such file or directory
lampp/var/mysql/cdcol/cds.frm
tar: lampp/var/mysql/cdcol/cds.frm: Cannot open: No such file or directory
lampp/var/mysql/mysql/
tar: lampp/var/mysql/mysql: Cannot mkdir: No such file or directory
lampp/var/mysql/mysql/columns_priv.MYD
tar: lampp/var/mysql/mysql/columns_priv.MYD: Cannot open: No such file or directory
lampp/var/mysql/mysql/columns_priv.frm
tar: lampp/var/mysql/mysql/columns_priv.frm: Cannot open: No such file or directory
lampp/var/mysql/mysql/user.MYI
tar: lampp/var/mysql/mysql/user.MYI: Cannot open: No such file or directory
lampp/var/mysql/mysql/db.MYI
tar: lampp/var/mysql/mysql/db.MYI: Cannot open: No such file or directory
lampp/var/mysql/mysql/host.MYI
tar: lampp/var/mysql/mysql/host.MYI: Cannot open: No such file or directory
lampp/var/mysql/mysql/func.MYI
tar: lampp/var/mysql/mysql/func.MYI: Cannot open: No such file or directory
lampp/var/mysql/mysql/func.MYD
tar: lampp/var/mysql/mysql/func.MYD: Cannot open: No such file or directory
lampp/var/mysql/mysql/db.MYD
tar: lampp/var/mysql/mysql/db.MYD: Cannot open: No such file or directory
lampp/var/mysql/mysql/db.frm
tar: lampp/var/mysql/mysql/db.frm: Cannot open: No such file or directory
lampp/var/mysql/mysql/time_zone_leap_second.MYD
tar: lampp/var/mysql/mysql/time_zone_leap_second.MYD: Cannot open: No such file or directory
lampp/var/mysql/mysql/help_keyword.MYD
tar: lampp/var/mysql/mysql/help_keyword.MYD: Cannot open: No such file or directory
lampp/var/mysql/mysql/help_category.MYI
tar: lampp/var/mysql/mysql/help_category.MYI: Cannot open: No such file or directory
lampp/var/mysql/mysql/help_topic.MYD
tar: lampp/var/mysql/mysql/help_topic.MYD: Cannot open: No such file or directory
lampp/var/mysql/mysql/help_topic.frm
tar: lampp/var/mysql/mysql/help_topic.frm: Cannot open: No such file or directory
lampp/var/mysql/mysql/help_keyword.MYI
tar: lampp/var/mysql/mysql/help_keyword.MYI: Cannot open: No such file or directory
lampp/var/mysql/mysql/help_relation.MYD
tar: lampp/var/mysql/mysql/help_relation.MYD: Cannot open: No such file or directory
lampp/var/mysql/mysql/help_relation.MYI
tar: lampp/var/mysql/mysql/help_relation.MYI: Cannot open: No such file or directory
lampp/var/mysql/mysql/help_relation.frm
tar: lampp/var/mysql/mysql/help_relation.frm: Cannot open: No such file or directory
lampp/var/mysql/mysql/host.MYD
tar: lampp/var/mysql/mysql/host.MYD: Cannot open: No such file or directory
lampp/var/mysql/mysql/user.MYD
tar: lampp/var/mysql/mysql/user.MYD: Cannot open: No such file or directory
lampp/var/mysql/mysql/user.frm
tar: lampp/var/mysql/mysql/user.frm: Cannot open: No such file or directory
lampp/var/mysql/mysql/help_topic.MYI
tar: lampp/var/mysql/mysql/help_topic.MYI: Cannot open: No such file or directory
lampp/var/mysql/mysql/host.frm
tar: lampp/var/mysql/mysql/host.frm: Cannot open: No such file or directory
lampp/var/mysql/mysql/func.frm
tar: lampp/var/mysql/mysql/func.frm: Cannot open: No such file or directory
lampp/var/mysql/mysql/proc.MYI
tar: lampp/var/mysql/mysql/proc.MYI: Cannot open: No such file or directory
lampp/var/mysql/mysql/proc.MYD
tar: lampp/var/mysql/mysql/proc.MYD: Cannot open: No such file or directory
lampp/var/mysql/mysql/time_zone.MYD
tar: lampp/var/mysql/mysql/time_zone.MYD: Cannot open: No such file or directory
lampp/var/mysql/mysql/procs_priv.MYI
tar: lampp/var/mysql/mysql/procs_priv.MYI: Cannot open: No such file or directory
lampp/var/mysql/mysql/procs_priv.MYD
tar: lampp/var/mysql/mysql/procs_priv.MYD: Cannot open: No such file or directory
lampp/var/mysql/mysql/tables_priv.MYD
tar: lampp/var/mysql/mysql/tables_priv.MYD: Cannot open: No such file or directory
lampp/var/mysql/mysql/tables_priv.frm
tar: lampp/var/mysql/mysql/tables_priv.frm: Cannot open: No such file or directory
lampp/var/mysql/mysql/procs_priv.frm
tar: lampp/var/mysql/mysql/procs_priv.frm: Cannot open: No such file or directory
lampp/var/mysql/mysql/proc.frm
tar: lampp/var/mysql/mysql/proc.frm: Cannot open: No such file or directory
lampp/var/mysql/mysql/time_zone.MYI
tar: lampp/var/mysql/mysql/time_zone.MYI: Cannot open: No such file or directory
lampp/var/mysql/mysql/time_zone_transition_type.MYD
tar: lampp/var/mysql/mysql/time_zone_transition_type.MYD: Cannot open: No such file or directory
lampp/var/mysql/mysql/time_zone_leap_second.MYI
tar: lampp/var/mysql/mysql/time_zone_leap_second.MYI: Cannot open: No such file or directory
lampp/var/mysql/mysql/time_zone_leap_second.frm
tar: lampp/var/mysql/mysql/time_zone_leap_second.frm: Cannot open: No such file or directory
lampp/var/mysql/mysql/time_zone_name.MYD
tar: lampp/var/mysql/mysql/time_zone_name.MYD: Cannot open: No such file or directory
lampp/var/mysql/mysql/time_zone_name.MYI
tar: lampp/var/mysql/mysql/time_zone_name.MYI: Cannot open: No such file or directory
lampp/var/mysql/mysql/time_zone_name.frm
tar: lampp/var/mysql/mysql/time_zone_name.frm: Cannot open: No such file or directory
lampp/var/mysql/mysql/time_zone_transition.MYD
tar: lampp/var/mysql/mysql/time_zone_transition.MYD: Cannot open: No such file or directory
lampp/var/mysql/mysql/time_zone_transition.MYI
tar: lampp/var/mysql/mysql/time_zone_transition.MYI: Cannot open: No such file or directory
lampp/var/mysql/mysql/time_zone_transition.frm
tar: lampp/var/mysql/mysql/time_zone_transition.frm: Cannot open: No such file or directory
lampp/var/mysql/mysql/time_zone_transition_type.MYI
tar: lampp/var/mysql/mysql/time_zone_transition_type.MYI: Cannot open: No such file or directory
lampp/var/mysql/mysql/time_zone_transition_type.frm
tar: lampp/var/mysql/mysql/time_zone_transition_type.frm: Cannot open: No such file or directory
lampp/var/mysql/mysql/columns_priv.MYI
tar: lampp/var/mysql/mysql/columns_priv.MYI: Cannot open: No such file or directory
lampp/var/mysql/mysql/help_keyword.frm
tar: lampp/var/mysql/mysql/help_keyword.frm: Cannot open: No such file or directory
lampp/var/mysql/mysql/help_category.frm
tar: lampp/var/mysql/mysql/help_category.frm: Cannot open: No such file or directory
lampp/var/mysql/mysql/tables_priv.MYI
tar: lampp/var/mysql/mysql/tables_priv.MYI: Cannot open: No such file or directory
lampp/var/mysql/mysql/help_category.MYD
tar: lampp/var/mysql/mysql/help_category.MYD: Cannot open: No such file or directory
lampp/var/mysql/mysql/time_zone.frm
tar: lampp/var/mysql/mysql/time_zone.frm: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/
tar: lampp/var/mysql/phpmyadmin: Cannot mkdir: No such file or directory
lampp/var/mysql/phpmyadmin/pma_bookmark.frm
tar: lampp/var/mysql/phpmyadmin/pma_bookmark.frm: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_relation.MYI
tar: lampp/var/mysql/phpmyadmin/pma_relation.MYI: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_relation.MYD
tar: lampp/var/mysql/phpmyadmin/pma_relation.MYD: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_column_info.frm
tar: lampp/var/mysql/phpmyadmin/pma_column_info.frm: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_history.MYD
tar: lampp/var/mysql/phpmyadmin/pma_history.MYD: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_table_coords.MYI
tar: lampp/var/mysql/phpmyadmin/pma_table_coords.MYI: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_history.frm
tar: lampp/var/mysql/phpmyadmin/pma_history.frm: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_bookmark.MYI
tar: lampp/var/mysql/phpmyadmin/pma_bookmark.MYI: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_table_info.MYI
tar: lampp/var/mysql/phpmyadmin/pma_table_info.MYI: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_relation.frm
tar: lampp/var/mysql/phpmyadmin/pma_relation.frm: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_column_info.MYI
tar: lampp/var/mysql/phpmyadmin/pma_column_info.MYI: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_table_coords.frm
tar: lampp/var/mysql/phpmyadmin/pma_table_coords.frm: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_table_info.MYD
tar: lampp/var/mysql/phpmyadmin/pma_table_info.MYD: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_designer_coords.MYI
tar: lampp/var/mysql/phpmyadmin/pma_designer_coords.MYI: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_table_info.frm
tar: lampp/var/mysql/phpmyadmin/pma_table_info.frm: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_pdf_pages.MYD
tar: lampp/var/mysql/phpmyadmin/pma_pdf_pages.MYD: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/db.opt
tar: lampp/var/mysql/phpmyadmin/db.opt: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_pdf_pages.frm
tar: lampp/var/mysql/phpmyadmin/pma_pdf_pages.frm: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_history.MYI
tar: lampp/var/mysql/phpmyadmin/pma_history.MYI: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_pdf_pages.MYI
tar: lampp/var/mysql/phpmyadmin/pma_pdf_pages.MYI: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_designer_coords.frm
tar: lampp/var/mysql/phpmyadmin/pma_designer_coords.frm: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_table_coords.MYD
tar: lampp/var/mysql/phpmyadmin/pma_table_coords.MYD: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_bookmark.MYD
tar: lampp/var/mysql/phpmyadmin/pma_bookmark.MYD: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_column_info.MYD
tar: lampp/var/mysql/phpmyadmin/pma_column_info.MYD: Cannot open: No such file or directory
lampp/var/mysql/phpmyadmin/pma_designer_coords.MYD
tar: lampp/var/mysql/phpmyadmin/pma_designer_coords.MYD: Cannot open: No such file or directory
lampp/var/mysql/test/
tar: lampp/var/mysql/test: Cannot mkdir: No such file or directory
lampp/var/mysql/test/testaa.MYD
tar: lampp/var/mysql/test/testaa.MYD: Cannot open: No such file or directory
lampp/var/mysql/test/testaa.MYI
tar: lampp/var/mysql/test/testaa.MYI: Cannot open: No such file or directory
lampp/var/mysql/test/testaa.frm
tar: lampp/var/mysql/test/testaa.frm: Cannot open: No such file or directory
lampp/var/mysql/test/testab.MYD
tar: lampp/var/mysql/test/testab.MYD: Cannot open: No such file or directory
lampp/var/mysql/test/testab.MYI
tar: lampp/var/mysql/test/testab.MYI: Cannot open: No such file or directory
lampp/var/mysql/test/testab.frm
tar: lampp/var/mysql/test/testab.frm: Cannot open: No such file or directory
lampp/var/mysql/test/testac.MYI
tar: lampp/var/mysql/test/testac.MYI: Cannot open: No such file or directory
lampp/var/mysql/test/testae.MYD
tar: lampp/var/mysql/test/testae.MYD: Cannot open: No such file or directory
lampp/var/mysql/test/testad.MYI
tar: lampp/var/mysql/test/testad.MYI: Cannot open: No such file or directory
lampp/var/mysql/test/testad.MYD
tar: lampp/var/mysql/test/testad.MYD: Cannot open: No such file or directory
lampp/var/mysql/test/testaf.MYD
tar: lampp/var/mysql/test/testaf.MYD: Cannot open: No such file or directory
lampp/var/mysql/test/testae.MYI
tar: lampp/var/mysql/test/testae.MYI: Cannot open: No such file or directory
lampp/var/mysql/test/testae.frm
tar: lampp/var/mysql/test/testae.frm: Cannot open: No such file or directory
lampp/var/mysql/test/testah.MYD
tar: lampp/var/mysql/test/testah.MYD: Cannot open: No such file or directory
lampp/var/mysql/test/testaf.MYI
tar: lampp/var/mysql/test/testaf.MYI: Cannot open: No such file or directory
lampp/var/mysql/test/testaf.frm
tar: lampp/var/mysql/test/testaf.frm: Cannot open: No such file or directory
lampp/var/mysql/test/testai.MYD
tar: lampp/var/mysql/test/testai.MYD: Cannot open: No such file or directory
lampp/var/mysql/test/testah.MYI
tar: lampp/var/mysql/test/testah.MYI: Cannot open: No such file or directory
lampp/var/mysql/test/testah.frm
tar: lampp/var/mysql/test/testah.frm: Cannot open: No such file or directory
lampp/var/mysql/test/testak.MYD
tar: lampp/var/mysql/test/testak.MYD: Cannot open: No such file or directory
lampp/var/mysql/test/testai.MYI
tar: lampp/var/mysql/test/testai.MYI: Cannot open: No such file or directory
lampp/var/mysql/test/testak.MYI
tar: lampp/var/mysql/test/testak.MYI: Cannot open: No such file or directory
lampp/var/mysql/test/testak.frm
tar: lampp/var/mysql/test/testak.frm: Cannot open: No such file or directory
lampp/var/mysql/test/testad.frm
tar: lampp/var/mysql/test/testad.frm: Cannot open: No such file or directory
lampp/var/mysql/test/testac.MYD
tar: lampp/var/mysql/test/testac.MYD: Cannot open: No such file or directory
lampp/var/mysql/test/testac.frm
tar: lampp/var/mysql/test/testac.frm: Cannot open: No such file or directory
lampp/var/mysql/test/testai.frm
tar: lampp/var/mysql/test/testai.frm: Cannot open: No such file or directory
lampp/var/mysql/test/testag.frm
tar: lampp/var/mysql/test/testag.frm: Cannot open: No such file or directory
lampp/var/mysql/test/testag.MYI
tar: lampp/var/mysql/test/testag.MYI: Cannot open: No such file or directory
lampp/var/mysql/test/testag.MYD
tar: lampp/var/mysql/test/testag.MYD: Cannot open: No such file or directory
lampp/var/proftpd/
tar: lampp/var/proftpd: Cannot mkdir: No such file or directory
lampp/var/proftpd/proftpd.delay
tar: lampp/var/proftpd/proftpd.delay: Cannot open: No such file or directory
lampp/var/run/
tar: lampp/var/run: Cannot mkdir: No such file or directory
lampp/RELEASENOTES
tar: lampp/RELEASENOTES: Cannot open: No such file or directory
lampp/lampp
tar: lampp/lampp: Cannot open: No such file or directory
lampp/libexec/
tar: lampp/libexec: Cannot mkdir: No such file or directory
tar: Error exit delayed from previous errors
ryan@ryan-desktop:~/Desktop$ /opt/lampp/lampp start
bash: /opt/lampp/lampp: No such file or directory
ryan@ryan-desktop:~/Desktop$ 

```

---

### Post by louieb on 2008-04-06
What command? Need to know exactly what you typed.
I'm guessing you ran [B]tar ....
[/B]
You need to run the command with superuser privileges so
change that to [B]sudo tar ...

[/B]

---

### Post by ImThatNerd on 2008-04-06
Okay I installed XAMPP.

When I enter [http://localhost/](http://localhost/)

It just shows Index of /  with apache2-default/    folder inside and when I click it it says 'It Works!'.

So now what do I do? How can I upload things and actually view them?

---

### Post by louieb on 2008-04-06
Nice - you got it up and running. Can't remember where XAMPP puts what Apache calls the document root. Or where it put the apache2.conf file either. But in Ubuntu LAMP install the document root is /var/www/ and the configuration files are in /etc/apache2.

Now the fun really begins. Find the file apache2.conf and start with links I gave you earlier. The apache server has a lot of options. I went on brain overload when I 1st set one up.

---

