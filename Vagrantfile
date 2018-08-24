ENV['VAGRANT_DEFAULT_PROVIDER'] = 'docker'

VAGRANTFILE_API_VERSION = "2"

CURRENT_DIR = Dir.pwd

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "desktop", autostart: false do |feeder|
      feeder.vm.provider "docker" do |docker|
          docker.name = "desktop"
          # docker.image = "queeno/ubuntu-desktop"
          # docker.image = "queeno/ubuntu-desktop"
          docker.build_dir = "."
          docker.remains_running = true

          docker.ports = [ "5901:5901" ]
          docker.expose = [ 5901 ]

          docker.volumes = [
            CURRENT_DIR + ":/vinik_desktop"
          ]
      end
  end

  config.vm.define "firefox", autostart: false do |firefox|
      firefox.vm.provider "docker" do |docker|
          docker.name = "firefox"
          docker.image = "vinik/firefox"
          # docker.build_dir = "apps/firefox/"
          docker.remains_running = true

          docker.env = {
              :DISPLAY => ":0.0"
          }

          docker.volumes = [
              "/tmp/.X11-unix:/tmp/.X11-unix"
          ]
      end
  end

end
