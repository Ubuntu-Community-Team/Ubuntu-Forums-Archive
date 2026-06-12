---
title: "Nvidia installer script for Ubuntu Dapper Drake"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by kurian on 2007-07-30
hi,

This script is used  for automating the installation of nvidia driver in the ubuntu dapper drake. The script automatically identifies ur nvidia driver and installs the appropriate package...


just run  : sudo ./nvidia.pl
or sudo perl nvidia.pl


please send me any bugs in this script....

plz make a file called nvidia.pl by cutting and pasting the following code :

#start
 
 #!/usr/local/bin/perl
 
open(f1,"/etc/apt/sources.list") and @a=<f1>;
for $i(0..$#a)
 {
  ($a[$i]=~/^\# deb/) and @a[$i]=substr(@a[$i],2,);
 }
close f1;
open(f2,">/etc/apt/sources.list") or die "$!";
print f2 @a and close f2;
 print "wait while apt-get is updated\n";
print `sudo apt-get update`; 

open(f3,"/etc/X11/xorg.conf") and @bb=<f3>;

@legacy=("NVIDIA chip name Device PCI ID",
"RIVA TNT 0x0020",
"RIVA TNT2/TNT2 Pro 0x0028","RIVA TNT2 Ultra 0x0029",
"Vanta/Vanta LT 0x002C",
"RIVA TNT2 Model 64/Model 64 Pro 0x002D",
"Aladdin TNT2 0x00A0",
"GeForce 256 0x0100",
"GeForce DDR 0x0101",
"Quadro 0x0103",
"GeForce2 GTS/GeForce2 Pro 0x0150","GeForce2 Ti 0x0151",
"GeForce2 Ultra 0x0152","Quadro2 Pro 0x0153",
"GeForce4 460 Go 0x0177","NV31M [GeForce FX Go5600] (rev a1) 0x031a");

for $i(0..$#bb)
   {
    $bb[$i]=~/Identifier.+NVIDIA.+\[(.+)\]/ and $driver=$1;
   }
$drivername="nvidia-glx";
for $i(0..$#legacy)
  {
    if($legacy[$i] eq $driver)
         {
            $drivername="nvidia-glx-legacy";
         }
  }
close f3;

print "downloading and installing the nvidia driver";
print `sudo apt-get install $drivername`;
print `sudo nvidia-glx-config enable`;
for $i(0..$#bb)
   {
    $bb[$i]=~/Driver.+\"nv\"/ and $bb[$i]=~s/nv/nvidia/;

  }
open(f4,">/etc/X11/xorg.conf");
print f4 @bb;
print "\n Successfully completed the task: Restart your xserver";


#stop

---

### Post by rainbowed_man on 2007-07-30
Hi.

Uh, after cursorily reading the code, I found a bug.

$drivername will NOT be defined if the driver from the xorg.conf is not in the array which it searches on.

Also, please note that the Restricted Drivers Manager is much more robust and more tested than your script.

- Kyle Brooks

---

### Post by kurian on 2007-07-31
Thanks for  looking to the script... i have first of all given $drivername="nvidia-glx " this will solve ur problem. I think u might not have seen this line,

$drivername="nvidia-glx";
for $i(0..$#legacy)
{
if($legacy[$i] eq $driver)
{
$drivername="nvidia-glx-legacy";
}
}

I have made this script not for ubuntu feisty fawn ( Restricted driver manager is only available in feisty fawn) but for ubuntu dapper drake which dont have such a good driver manager.

---

### Post by dpar on 2007-07-31
> I have made this script not for ubuntu feisty fawn ( Restricted driver manager is only available in feisty fawn) but for ubuntu dapper drake which dont have such a good driver manager.


Envy?

---

### Post by dragonwings on 2007-07-31
hi im not sure if Dapper Drake is 6.06lts but for  my old 6.06lts i got driver from site below

[http://www.cs.cornell.edu/~djm/ubuntu/#nivdia-driver](http://www.cs.cornell.edu/~djm/ubuntu/#nivdia-driver)

this could be help or none at all to you guys ??????but it worked on my old 6.06lts install
im now using 7.04.

---

### Post by kurian on 2007-07-31
yea dapper drake is 6.06 itself by the way this script is just an alternative script to envy...thats all.

---

