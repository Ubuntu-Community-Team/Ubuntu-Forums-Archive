---
title: "problems in installing compiz"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by ojasvi rajpal on 2006-10-28
I am trying to install compiz using the post "http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29"
but I am facing the following problems ;

1.) my x.conf has no Busid tag 
Quote starts
"Section "Device"
	Identifier	"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

    * Replace with the following lines, leaving the Identifier and BusID as it is 

"
quote ends

2.)when I install compiz it gives the following error 
"
ojasvi@Dreams:~$ sudo apt-get install compiz
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-plugins (>= 0.2) but it is not going to be installed
E: Broken packages
"
Plzzzz help ](*,)

---

