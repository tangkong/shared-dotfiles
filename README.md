# shared-dotfiles

Shared configuration useful for PCDS engineers: "dot" files such as bash
configuration (.bashrc) and SSH configuration (.ssh/config).

## On-site and off-site

Some configuration is broken up into "on-site" versus "off-site" here.

1. The off-site configuration is meant for your laptop or machine you use at home
   to connect to the PCDS network by way of SSH, OpenVPN, or similar.
   It works well on SLAC WiFi, too, so you don't need to switch back and forth.
2. The on-site configuration is meant to be used on PCDS machines like pslogin
   and psbuild-rhel7.  You have a shared home storage space on these machines,
   so you will only need to install it once.

## How to use these

### Trial run

You can try parts of these settings without installing anything by doing the
following:

```bash
$ ssh psbuild-rhel7
$ git clone git@github.com:pcdshub/shared-dotfiles dotfiles
$ cd dotfiles
$ ./try_me_onsite.sh
# Then read the instructions in the script output.
```

Please note that this only applies to the bash configuration and not the SSH,
git, vim, and other provided configurations here.

### Out-of-the-box

To link the scripts here and use them every time when you login:

```bash
$ ssh psbuild-rhel7
$ git clone git@github.com:pcdshub/shared-dotfiles dotfiles
$ cd dotfiles
$ bash use_dotfiles.sh
```

You will only need to do this once.

### Advanced or custom usage

Advanced users may want to start their own dotfiles repository based on this one.
You can then version-control your dotfiles, simply soft-linking the files
in your fork.  For example:

1. Fork pcdshub/shared-dotfiles to your-user/shared-dotfiles
2.
```bash
$ ssh psbuild-rhel7
$ cd   # <-- work in your home directory
$ git clone git@github.com:your-user/shared-dotfiles dotfiles
$ ln -s dotfiles/bashrc .bashrc
```

## SSH configuration

SSH configurations for on-site versus off-site usage exist.

The ``use_dotfiles.sh`` script assumes an on-site configuration for now,
so it's recommended to run it on psbuild-rhel7 or similar.
