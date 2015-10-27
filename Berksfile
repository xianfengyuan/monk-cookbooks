branch = 'dev'

sheer_git_url = 'git@github.com:/xianfengyuan'

sheer_cookbooks = "
build-essential
runit
monkeybar
".split

# Include Opsworks Cookbooks
opsworks_cb_path = '/opt/aws/opsworks/current/cookbooks'
opsworks_cookbooks = Dir[opsworks_cb_path + '/*'].select { |f| File.directory?(f) }.map { |f| File.basename(f) }

# Remove any opsworks cookbooks that we use
opsworks_cookbooks -= sheer_cookbooks

# Get all of the opworks cookbooks
opsworks_cookbooks.each do |cb|
  cookbook(cb, path: File.join(opsworks_cb_path, cb))
end

# Get all custom cookbooks
sheer_cookbooks.each do |thiscookbook|
  cookbook(thiscookbook, git: sheer_git_url + '/chef_' + thiscookbook, branch: branch)
end
