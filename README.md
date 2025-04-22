# Dotfiles

This repository contains my personal dotfiles, used to configure my development environment on macOS. It includes settings for Zsh, Git, macOS preferences, and more, optimized for productivity and a clean workflow. This setup is heavily inspired by and forked from Jeff Geerling's dotfiles.

## Purpose

These dotfiles are designed to:

- Set up a consistent development environment with tools like Visual Studio Code, Zsh, and Git.
- Support separate configurations for personal and work-related projects.
- Provide a streamlined setup for macOS, including Finder, Dock, and performance tweaks.

## Files

- **`.zshrc`**: Configures the Zsh shell with aliases, functions, and a custom prompt (using Oh My Zsh and Powerlevel10k).
- **`.osx`**: Customizes macOS settings, such as Finder preferences, Dock behavior, and performance optimizations.
- **`.gitconfig`**: Configures Git with aliases, VSCode as the editor and merge tool, and conditional includes for personal and work projects.
- **`.gitignore`**: Excludes sensitive files (e.g., `.gitconfig-work`, `.ssh/*`) from being committed.

## Installation

1. **Clone the repository**:

   ```bash
   git clone https://github.com/rafasousa/dotfiles.git ~/dotfiles
   cd ~/dotfiles
   ```

2. **Install dependencies** (macOS):

   - Install [Homebrew](https://brew.sh/):
     ```bash
     /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
     ```
   - Install required tools:
     ```bash
     brew install zsh git visual-studio-code
     ```
   - Install Oh My Zsh:
     ```bash
     sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
     ```
   - Install Powerlevel10k:
     ```bash
     git clone https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
     ```

3. **Set up dotfiles**:

   - Run the installation script (adjust `install.sh` if provided, or create symlinks manually):
     ```bash
     ln -sf ~/dotfiles/.zshrc ~/.zshrc
     ln -sf ~/dotfiles/.osx ~/.osx
     ln -sf ~/dotfiles/.gitconfig ~/.gitconfig
     ln -sf ~/dotfiles/.gitignore ~/.gitignore
     ```
   - Apply macOS settings:
     ```bash
     chmod +x ~/.osx
     ~/.osx
     ```

4. **Restart your shell**:
   ```bash
   source ~/.zshrc
   ```

## Work Configuration

To support separate Git identities for personal and work projects, this setup uses conditional includes in `.gitconfig`. For work projects, create a local `~/.gitconfig-work` file (not included in this repository) with your work credentials.

Example `~/.gitconfig-work`:

```ini
[user]
    name = Your Name
    email = your.work.email@company.com
```

Place work-related repositories in `~/projects/work/` to automatically apply the work configuration. The `.gitconfig-work` file is private and excluded via `.gitignore` to prevent accidental exposure.

## Customization

- **Zsh**: Modify `.zshrc` to add your own aliases or functions. See the file for examples (e.g., aliases for Git, Docker, or ArchiCAD).
- **macOS**: Adjust `.osx` to tweak Finder, Dock, or performance settings to your preference.
- **Git**: Add custom Git aliases in `.gitconfig` or `.gitconfig-personal` for personal projects.

## Notes

- Ensure sensitive files (e.g., `.gitconfig-work`, `.ssh/config`) are excluded from the repository via `.gitignore`.
- Some macOS settings in `.osx` require a logout/login to take effect.
- This setup assumes a macOS environment with Zsh as the default shell.

## Credits

This repository is based on and inspired by [Jeff Geerling's dotfiles](https://github.com/geerlingguy/dotfiles). Many thanks to Jeff for providing a solid foundation for this setup.

## License

This repository is licensed under the [MIT License](LICENSE).
