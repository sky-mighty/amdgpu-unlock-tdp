# What is this?

_First and foremost, I'm not responsible if you set your power limits to 500W and burn your house down. Overclocking is dangerous; do not use these patches unless you know what you're doing._

This set of kernel patches will set the min and max power limits of most AMD GPUs on your system to 0 and 500W, while letting you configure what you exactly want via sysfs.

[LACT](https://github.com/ilya-zlobintsev/LACT) works flawlessly with this kernel patch.

# How do I install this?

Exact instructions will depend on your distro. In a nutshell, you'll need to compile your own kernel with these patces applied and add `amdgpu.ignore_pcap=1` to your kernel parameters.

I've tested this on Gentoo, running on 6.18.41 as of writing. I followed this wiki page after applying my patches to the source: https://wiki.gentoo.org/wiki/Kernel/Upgrade#Manual_build_and_installation

I can't provide exact instructions for everyone; this is highly system-dependent and these patches are mainly meant for people not afraid to get their hands dirty.

# What hardware can this unlock?

Honestly, I'm not sure. AMD realized the possibility of kernel-level unlocks somewhere around 2024. Here's what I tried:

- 5700XT: PL's completely unlocked.
- W6800: PL's completely unlocked. [Benchmark results](https://openbenchmarking.org/result/2511146-NE-XD270741367)
- R9700: Minimum PL sort of unlocked (can't go down to zero) and maximum PL stuck at 332w (exactly 10% above). I'm pretty sure I've hit the checks present on the GPU.

Essentially, AMD switched up their power management to give more control to their GPUs. I think this is done at the SMU level; hacking that will be a whole different ordeal that's out of scope for these kernel patches.

As you'll see from the benchmark results, I've been sitting on these kernel patches for almost a year... it's time to set them free :)

# Help! I can't apply these patches!

I'll be extremely real with you, I wrote these over a year ago and I've been using my unlocked cards to run LLMs and agents that apply these patches for me with each LTS release. PR's are more than welcome ;)
