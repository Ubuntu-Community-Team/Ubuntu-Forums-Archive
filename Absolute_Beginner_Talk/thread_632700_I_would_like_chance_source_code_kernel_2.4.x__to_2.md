---
title: "I would like chance source code kernel 2.4.x  to 2.6.21.1,how to chance source?"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by riquelme on 2007-12-05
-I have source code of C language and it run kernel 2.4.X ,I would like chance kernel to 2.6.21.1 How to fix source code ? because i run on kernel 2.6.21.1 result error 
-I have example source code  


#include <linux/module.h>
#include <linux/kernel.h>
#include <linux/errno.h>    
#include <linux/fs.h>       
#include <linux/ioctl.h>
#include <linux/pci.h>
#include </usr/src/kernels/2.6.21-1.3194.fc7-i686/include/asm-generic/uaccess.h>
#include <stdio.h>
#include "my_pci.h"

#ifdef MODULE
#else
#define MOD_INC_USE_COUNT
#define MOD_DEC_USE_COUNT
#endif


MODULE_LICENSE("GPL");

#ifndef CONFIG_PCI
#error "This driver needs PCI support to be available"
#endif

/* vendor and device ID*/
#define MY_PCI_VENDOR_ID      0x8086
#define MY_PCI_DEVICE_ID      0x2570

/* major number for the char device file /dev/my_pci */
#define MY_PCI_MAJOR 240

/* name for the driver */
#define MY_PCI_NAME "my_pci"

/* pci_dev structure */
struct pci_dev *my_pci_dev;

/* The virtual address of the base address */
char *my_pci_virt_addr;


struct file_operations {
   struct module *owner;
   loff_t       (*llseek)    (struct file *, loff_t, int);
   ssize_t    (*read)    (struct file *, char *, size_t, loff_t *);
   ssize_t    (*write)    (struct file *, const char *, size_t, loff_t *);
   unsigned int    (*poll)    (struct file *, struct poll_table_struct *);
   int       (*ioctl)    (struct inode *, struct file *, unsigned int, unsigned long);
   int       (*mmap)    (struct file *, struct vm_area_struct *);
   int       (*open)    (struct inode *, struct file *);
   int       (*flush)    (struct file *);
   int       (*release)    (struct inode *, struct file *);
   int       (*fsync)    (struct file *, struct dentry *, int datasync);
   int       (*fasync)    (int, struct file *, int);
   int       (*lock)    (struct file *, int, struct file_lock *);
   ssize_t    (*readv)   (struct file *, const struct iovec *, unsigned long, loff_t *);
   ssize_t    (*writev)    (struct file *, const struct iovec *, unsigned long, loff_t *);
};


/* open function */
static int my_pci_open(struct inode *inode,struct file *file)
{
   /* increment the module count */
   MOD_INC_USE_COUNT;
   return 0;
};


/* close function */
static int my_pci_release(struct inode *inode , struct file *file)
{
   /*decrement the module count*/
   MOD_DEC_USE_COUNT;
   return 0;
};


/*ioctl-function*/
static int my_pci_ioctl(struct inode *inode,struct file *file,unsigned int index,unsigned long arg)
{
   if (index == REG_CMD || index == REG_CTRL || index == REG_WDATA) {
   writel (arg, my_pci_virt_addr + (index << 2) );
   return 0; /* ok */
   }
   
   if (index == REG_STATUS || index == REG_RDATA){
   return put_user(
      readl (my_pci_virt_addr + (index << 2) ),
      (unsigned long *)arg );
   }

   if ( (index >> 17) & 1U) {
   writel( arg, my_pci_virt_addr + ((index & 0x0fff) << 2) );
   return 0; /* ok */
   }
   
   if ( (index >> 18) & 1U) {
   return put_user(
      readl( my_pci_virt_addr + ((index & 0x0fff) << 2) ),
      (unsigned long *)arg );
   }

   /* invalid ioctl commands*/
   return -EIO;
};

static ssize_t my_pci_write(struct file *filp, const char *buf, size_t _count, loff_t *f_pos)
{
   unsigned long mem_len = pci_resource_len(my_pci_dev,   0);
   printk("PCI-Board: write mem_len=%ld, count=%lu, f_pos=%lu\n", mem_len,_count,*f_pos);
   printk("    my_pci_virt_addr=%lx\n",my_pci_virt_addr );

   /* check address range */
   if ((*f_pos + _count) > mem_len){
   return -EFAULT;
   }
   
   if (copy_from_user(my_pci_virt_addr + *f_pos, buf, _count)){
   return -EFAULT;
   }
   
   *f_pos += _count;
   return _count;
}


static ssize_t my_pci_read (struct file *filp, char *buf,size_t count , loff_t *f_pos)
{
   unsigned long mem_len = pci_resource_len(my_pci_dev, 0);
   printk("PCI-Board: read mem_len=%ld, count=%lu, f_pos=%lu\n", mem_len, count, *f_pos);
   printk("   my_pci_virt_addr=%lx\n", (long unsigned)my_pci_virt_addr );

   /* check address range */
   if (*f_pos >= mem_len) {
   return 0;
   }

   /* check address range */
   if ((*f_pos + count ) > mem_len ){
   count = mem_len - *f_pos;
   }

   if (copy_to_user (buf, my_pci_virt_addr + *f_pos, count)) {
   return -EFAULT;
   }
   
   *f_pos += count;
   return count;
}

static struct file_operations my_pci_fops = {
   ioctl      : my_pci_ioctl,
   open      : my_pci_open,
   release      : my_pci_release,
   write      : my_pci_write,
   read      : my_pci_read,
};


void cleanup_module(void)
{
   unregister_chrdev(MY_PCI_MAJOR, MY_PCI_NAME);

   iounmap (my_pci_virt_addr);

   release_mem_region(
      pci_resource_start(my_pci_dev, 0),
      pci_resource_len(my_pci_dev , 0)
   );
}

int init_module (void)
{
   int result;
   my_pci_dev = NULL;

   if (!pci_present()) {
   printk ("PCI-Board: no pci-devices found.\n");
   result = -ENODEV;
   goto exit0;
   }

   if (register_chrdev(MY_PCI_MAJOR, MY_PCI_NAME,&my_pci_fops) != 0) {
   printk ("PCI-Board: unable to get major %d\n", MY_PCI_MAJOR );
   result = -EINVAL;
   goto exit0;
   }

   my_pci_dev = pci_find_device (   MY_PCI_VENDOR_ID,
               MY_PCI_DEVICE_ID, my_pci_dev);

   if (my_pci_dev == NULL) {
   printk ("PCI-Board: card not present \n");
   result = -EIO;
   goto exit1;
   }

    if (pci_enable_device (my_pci_dev)) {
   printk ("PCI-Board: unable to enable card\n");
   result = -EIO;
   goto exit1;
   }
   
   if (!request_mem_region(pci_resource_start(my_pci_dev , 0),
            pci_resource_len(my_pci_dev, 0),
            MY_PCI_NAME ) )
   {
      printk ("PCI-Board: request_mem_region (0x%lx) failed\n",
         pci_resource_start(my_pci_dev,0) );
      result = -EBUSY;
      goto   exit1;
   }

   my_pci_virt_addr = ioremap (pci_resource_start(my_pci_dev,0),pci_resource_len(my_pci_dev,0) );
   printk ("PCI-Board: pci-card found at address 0x%lx\n",
      pci_resource_start (my_pci_dev, 0));
   return 0;

   exit1:
      unregister_chrdev(MY_PCI_MAJOR, MY_PCI_NAME);
   exit0:
      return result;

}


/*----------------------------------------------------------------------------------------*/

---

### Post by quandary on 2007-12-05
Absolute beginner talk is probably the wrong forum for your question. Check out the programming forum.

For your question:
Hm, you get any errors and warnings from the compiler?


Did you compile the new kernel and forgot to enable PCI support???

Here is how to get to a new kernel correctly:


cd /usr/src
wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.1.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.1.tar.bz2)
wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.1.tar.bz2.sign](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.1.tar.bz2.sign)


apt-get update
apt-get install kernel-package libncurses5-dev fakeroot wget bzip2


tar xjf linux-2.6.23.1.tar.bz2
ln -s linux-2.6.23.1 linux
cd /usr/src/linux

***
Apply patches here
***

cp /boot/config-`uname -r` ./.config
make menuconfig

*** Build the kernel
make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
*** Finished building the kernel

cd /usr/src
ls -l
*** On my test system they were called linux-image-2.6.23.1-custom_2.6.23.1-custom-10.00.Custom_i386.deb 
*** (which contains the actual kernel) and 
*** linux-headers-2.6.23.1-custom_2.6.23.1-custom-10.00.Custom_i386.deb 
*** (which contains files needed if you want to compile additional kernel modules later on). 

*** Install them
dpkg -i linux-image-2.6.23.1-custom_2.6.23.1-custom-10.00.Custom_i386.deb
dpkg -i linux-headers-2.6.23.1-custom_2.6.23.1-custom-10.00.Custom_i386.deb

*** (You can now even transfer the two .deb files to other Ubuntu systems 
*** and install them there exactly the same way, 
*** which means you don't have to compile the kernel there again.)

vi /boot/grub/menu.lst



*** Now reboot the system:
shutdown -r now

*** If everything goes well, it should come up with the new kernel. 
*** You can check if it's really using your new kernel by running
uname -r

***This should display something like
--------------------
|                  |
| 2.6.23.1-custom  |
|                  |
--------------------

If the system doesn't start, restart it, and when you see this:
--------------------------------------------------
|                                                |
| GRUB Loading stage 1.5                         |
|                                                |
|                                                |           
| GRUB loading, please wait...                   |
| Press 'ESC' to enter the menu... 1    _        |
|                                                |
--------------------------------------------------

press ESC to enter the GRUB menu:
Select your old kernel and start the system. 
You can now try again to compile a working kernel. 
Don't forget to remove the two stanzas of the not-working kernel from /boot/grub/menu.lst.

---

