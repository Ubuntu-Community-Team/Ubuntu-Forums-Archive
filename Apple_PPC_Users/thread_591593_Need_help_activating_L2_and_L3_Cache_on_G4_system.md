---
title: "Need help activating L2 and L3 Cache on G4 system"
date: 2007-10-25
forum: Apple PPC Users
---

### Post by MJMullinII on 2007-10-25
Good day fellow Ubuntu's.

I have recently successfully installed Ubuntu 6.10 on a Power Mac 9600 I had kicking around but have a problem.

The machine has been upgraded with a G4 1 Ghz. processor upgrade from Sonnettech.com

It works beautifully in Mac OS 9.1 (using Sonnet's software to activate the L2 and L3 cache).  It even works OK in Mac OS X (using software to allow for install), again, using Sonnett's cache activation software.

However, I cannot find any information on the Web about activating the two caches under Linux.  Every website assumes when you talk about the G4 processor that you are using an upgrade in a machine that came from the factory with a G4, thereby not needing any special software to set it up.

I've read several places that there is a way to manually set the firmware settings in Linux so it will setup bot Caches (I can get the numbers from my Mac OS X install), but can find no place to manually enter them.

ANY help whatsoever would be greatly appreciated.

Good day to all.

---

### Post by bobby b on 2008-01-20
Setting the L2 cache is easy. Whichever method you use to pass in kernel command lines, do
l2cr=some value
in my case with the same G4 board it's
l2cr=0x8000000

It doesn't appear that there is a way to set l3 even though there is a l3 cache setting routine in the kernel. I hacked code into the kernel (after getting absolutely no help from the linuxppc-dev list).

It seems to work BUT I'm getting infrequent random lockups which I am trying to track down (it's not memory, that tested ok). The G4 cards are pretty touchy about PCI cards and I have a fully loaded 6 slot machine (S900). It could also be bad L3 cache on the sonnet board. My value for l3cr is supposedly 0x9f020300 (from the OSX cache setting routing in the console logs).

I wish I could figure out the exact meaning of the bits. The masks are in /usr/include/asm/reg.h

---

### Post by bobby b on 2008-01-23
Found the exact meaning for the L3CR bits with help from Sonnet. They are in the MPC7450 RISC Microprocessor Family Reference Manual on the Freescale website.

In arch/powerpc/kernel/setup_32.c
there is a routine to set the l2cr from a command line parameter. I just copied that and changed the references to create a set l3cr from a command line parameter.

/* Checks "l3cr=xxxx" command-line option */
int __init ppc_setup_l3cr(char *str)
{
        if (cpu_has_feature(CPU_FTR_L3CR)) {
                unsigned long val = simple_strtoul(str, NULL, 0);
                printk(KERN_INFO "haxx: l3cr set to %lx\n", val);
                _set_L3CR(0);           /* force invalidate by disable cache */
                _set_L3CR(val);         /* and enable it */
        }
        return 1;
}
__setup("l3cr=", ppc_setup_l3cr);

I'm not sure that "force invalidate" line is necessary for l3cr, I'm still working through the 7450 docs and the actual setting routine in the kernel.
_set_L3CR is in l2cr_6xx.S.

In my case at least, turning on the L3 cache from the command line speeds up my xbench scores considerably.

---

