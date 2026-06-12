---
title: "Gusty Install Erros"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Ketahazure on 2007-11-28
First and foremost greetings to all! Im very new to ubuntu and Ive been getting familurized with bash over these past 2 weeks or so. Sucsessfully installed ndiswrapper and got my linksys wifi card work so for a while i was feeling pretty good with my smooth transistion from windoze. well today im installing stuff and im getting crazy errors.


> 
ketahazure@inK3:/etc/apt$ sudo apt-get install netatalk
&#12497;&#12483;&#12465;&#12540;&#12472;&#12522;&#12473;&#12488;&#12434;&#35501;&#12415;&#36796;&#12435;&#12391;&#12356;&#12414;&#12377;... &#23436;&#20102;
&#20381;&#23384;&#38306;&#20418;&#12484;&#12522;&#12540;&#12434;&#20316;&#25104;&#12375;&#12390;&#12356;&#12414;&#12377;                
Reading state information... &#23436;&#20102;            
netatalk &#12399;&#12377;&#12391;&#12395;&#26368;&#26032;&#12496;&#12540;&#12472;&#12519;&#12531;&#12391;&#12377;&#12290;
&#12450;&#12483;&#12503;&#12464;&#12524;&#12540;&#12489;: 0 &#20491;&#12289;&#26032;&#35215;&#12452;&#12531;&#12473;&#12488;&#12540;&#12523;: 0 &#20491;&#12289;&#21066;&#38500;: 0 &#20491;&#12289;&#20445;&#30041;: 5 &#20491;&#12290;
3 &#20491;&#12398;&#12497;&#12483;&#12465;&#12540;&#12472;&#12364;&#23436;&#20840;&#12395;&#12452;&#12531;&#12473;&#12488;&#12540;&#12523;&#12414;&#12383;&#12399;&#21066;&#38500;&#12373;&#12428;&#12390;&#12356;&#12414;&#12379;&#12435;&#12290;
0B &#12398;&#12450;&#12540;&#12459;&#12452;&#12502;&#12434;&#21462;&#24471;&#12377;&#12427;&#24517;&#35201;&#12364;&#12354;&#12426;&#12414;&#12377;&#12290;
&#23637;&#38283;&#24460;&#12395;&#36861;&#21152;&#12391; 0B &#12398;&#12487;&#12451;&#12473;&#12463;&#23481;&#37327;&#12364;&#28040;&#36027;&#12373;&#12428;&#12414;&#12377;&#12290;
sdic-eijiro (2.1.3-13) &#12434;&#35373;&#23450;&#12375;&#12390;&#12356;&#12414;&#12377; ...
Building /usr/share/dict/eijiro.sdic ... /media/cdrom/eijiro/eijiro*.txt: No such file or directory
done.
Building suffix array (This will take a long long time) ... ERROR: text file mapping error.
dpkg: sdic-eijiro &#12398;&#20966;&#29702;&#20013;&#12395;&#12456;&#12521;&#12540;&#12364;&#30330;&#29983;&#12375;&#12414;&#12375;&#12383; (--configure):
 &#12469;&#12502;&#12503;&#12525;&#12475;&#12473; post-installation script &#12399;&#12456;&#12521;&#12540;&#32066;&#20102;&#12473;&#12486;&#12540;&#12479;&#12473; 1 &#12434;&#36820;&#12375;&#12414;&#12375;&#12383;
sdic-gene95 (2.1.3-13) &#12434;&#35373;&#23450;&#12375;&#12390;&#12356;&#12414;&#12377; ...
Prepare /tmp/gene95.lzh or /tmp/gene95.tar.gz or /tmp/gene95.tar.bz2 first.
dpkg: sdic-gene95 &#12398;&#20966;&#29702;&#20013;&#12395;&#12456;&#12521;&#12540;&#12364;&#30330;&#29983;&#12375;&#12414;&#12375;&#12383; (--configure):
 &#12469;&#12502;&#12503;&#12525;&#12475;&#12473; post-installation script &#12399;&#12456;&#12521;&#12540;&#32066;&#20102;&#12473;&#12486;&#12540;&#12479;&#12473; 1 &#12434;&#36820;&#12375;&#12414;&#12375;&#12383;
netatalk (2.0.3-6ubuntu1) &#12434;&#35373;&#23450;&#12375;&#12390;&#12356;&#12414;&#12377; ...
hostname: Unknown host
invoke-rc.d: initscript netatalk, action "start" failed.
dpkg: netatalk &#12398;&#20966;&#29702;&#20013;&#12395;&#12456;&#12521;&#12540;&#12364;&#30330;&#29983;&#12375;&#12414;&#12375;&#12383; (--configure):
 &#12469;&#12502;&#12503;&#12525;&#12475;&#12473; post-installation script &#12399;&#12456;&#12521;&#12540;&#32066;&#20102;&#12473;&#12486;&#12540;&#12479;&#12473; 1 &#12434;&#36820;&#12375;&#12414;&#12375;&#12383;
&#20197;&#19979;&#12398;&#12497;&#12483;&#12465;&#12540;&#12472;&#12398;&#20966;&#29702;&#20013;&#12395;&#12456;&#12521;&#12540;&#12364;&#30330;&#29983;&#12375;&#12414;&#12375;&#12383;:
 sdic-eijiro
 sdic-gene95
 netatalk
E: Sub-process /usr/bin/dpkg returned an error code (1)


Yes i do realize my locale is set to Japanese but aside from that its saying that my sdic-eijiro, sdic-gene95, and netatalk package install had errors. for some odd reason its looking in my cdrom drive. *> sdic-eijiro (2.1.3-13) &#12434;&#35373;&#23450;&#12375;&#12390;&#12356;&#12414;&#12377; ...
Building /usr/share/dict/eijiro.sdic ... /media/cdrom/eijiro/eijiro*.txt: No such file or directory Im not sure whats up with that. My guess is that you all (just guessing) not all too familure with the dsic-eijiro package. Its simply a file for the linux english-japanese dictionary. Some times when installing packages konsole will ask me if i want to isntall the japanese documention for the associated file but I was not asked in this instance. Thanks in advance!

---

### Post by gsiliceo on 2007-11-28
Lol im way too intimidated by those symbols to read

---

